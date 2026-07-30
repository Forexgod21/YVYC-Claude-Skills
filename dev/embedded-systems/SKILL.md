---
name: embedded-systems
category: dev
description: Use for firmware, microcontroller, and real-time systems work — C, C++, Rust embedded, ARM Cortex-M (M0/M0+/M3/M4/M7/M33), ESP32, ESP32-S3, RP2040, RP2350, STM32, nRF52/53, FreeRTOS, Zephyr RTOS, bare-metal, interrupt handlers, DMA, memory-mapped I/O, linker scripts, bootloaders, JTAG/SWD debugging, I2C, SPI, UART, CAN, USB, BLE, LoRa, and hardware bringup. Triggers on mentions of firmware, MCU, microcontroller, RTOS, ISR, DMA, bare-metal, HAL, or specific chips (STM32, ESP32, nRF, RP2040, SAMD, PIC32).
---

# Embedded Systems Expert

## Load Order
Read `shared-kernel/SKILL.md` first.

## Core Competencies

### Memory Layout
- `.text` (flash, read-only code)
- `.rodata` (flash, read-only data)
- `.data` (flash-initialized, copied to RAM on boot)
- `.bss` (RAM, zero-initialized)
- `.stack` (RAM, grows down)
- `.heap` (RAM, grows up — if used at all)
- Understand the linker script. Read it before trusting it.

### Interrupt Discipline
- ISRs are short, deterministic, and non-blocking
- No `malloc`, no `printf`, no floating-point unless FPU lazy stacking is configured
- No blocking on mutexes — use semaphores given from ISR or defer to task
- Priority assignment: higher priority = lower numeric value on Cortex-M
- Understand NVIC priority grouping (preempt priority vs subpriority)
- Nested interrupts are allowed but require stack budgeting

### DMA
- Cache maintenance is mandatory on Cortex-M7 with D-cache enabled:
  - Invalidate D-cache before DMA reads into buffer
  - Clean D-cache after CPU writes to DMA source buffer
- Align DMA buffers to cache line boundaries (32 bytes on Cortex-M7)
- Use non-cacheable MPU region for DMA buffers if cache maintenance is impractical

### RTOS Primitives
- **Task priorities**: static, assigned at creation, higher number = higher priority in FreeRTOS
- **Mutex vs semaphore**: mutex has priority inheritance, semaphore does not
- **Priority inversion**: use priority inheritance (mutex) or immediate ceiling
- **Queue vs message buffer**: queue is fixed-size items, message buffer is variable-length
- **Task notifications** are faster than semaphores for 1:1 signaling

### Power Management
- Sleep modes per MCU family — know the exit latency of each
- Wake sources: configure before entering sleep, verify with loopback test
- Clock tree: PLL, prescalers, peripheral clocks — changing one affects all
- Measure actual current draw with a `µCurrent` or Power Profiler Kit, not the datasheet

### Peripheral Bringup
Order matters:
1. Clock enable for the peripheral
2. GPIO alternate function configuration
3. Peripheral register configuration
4. NVIC enable (if using interrupts)
5. Peripheral enable

Verify with:
- Logic analyzer on SPI/I2C/UART lines
- Oscilloscope for timing-critical signals
- GPIO toggle at ISR entry/exit to measure ISR execution time

## Verification Gates

### Before Merging Firmware Changes
- `.map` file reviewed: flash usage, RAM usage, stack sizes
- Stack usage measured:
  - Static: GCC `-fstack-usage` + callgraph analysis
  - Runtime: stack watermarking (FreeRTOS `uxTaskGetStackHighWaterMark`)
- ISR execution time measured with GPIO toggle + oscilloscope
- No new warnings under `-Wall -Wextra -Werror`
- MISRA C rules respected if target is safety-critical

### Before Shipping
- Watchdog configured and fed from main loop, not from ISR
- Brownout detection enabled at appropriate threshold
- Bootloader verified: can recover from bricked app image
- OTA update path tested end-to-end if applicable
- Flash wear leveling if using internal flash for data storage

## Non-Negotiables

- No `printf` inside ISRs — ever
- No dynamic allocation after init in safety-critical paths
- All peripheral init functions return status codes, and callers check them
- Watchdog is configured before entering main loop
- No floating-point in ISRs unless FPU context save is explicitly configured
- All global state accessed from both ISR and task is `volatile` AND protected by critical section or lock-free primitive
- Interrupt-safe ring buffers use atomic head/tail pointers, not mutexes

## Common Failure Modes

| Symptom | Root Cause |
|---|---|
| HardFault on first peripheral use | Forgot to enable peripheral clock |
| HardFault with PC = garbage | Stack overflow — grow stack or reduce locals |
| HardFault with unaligned access | ARM requires alignment; cast through memcpy |
| DMA reads stale data | D-cache not invalidated before DMA read |
| DMA sees stale data from CPU | D-cache not cleaned after CPU write |
| Intermittent I2C NACK | Missing pull-ups or wrong timing at higher clock |
| UART garbled at high baud | Baud rate error > 2% — check clock tree |
| Task starvation | Lower-priority task never runs — check priority assignment |
| Priority inversion hang | Blocking on semaphore instead of priority-inheriting mutex |
| Current draw 10× datasheet | Peripheral left enabled in sleep, or floating GPIO |

## Deliverables

### Minimal Cortex-M Startup (conceptual — verify against your chip's startup)

```c
extern uint32_t _sidata, _sdata, _edata, _sbss, _ebss;
extern int main(void);

void Reset_Handler(void) {
    // Copy .data from flash to RAM
    uint32_t *src = &_sidata, *dst = &_sdata;
    while (dst < &_edata) *dst++ = *src++;

    // Zero .bss
    for (dst = &_sbss; dst < &_ebss; *dst++ = 0);

    // Enable FPU (Cortex-M4F/M7) — set CP10, CP11 full access
    SCB->CPACR |= (0xF << 20);

    // SystemInit() from CMSIS configures clock tree
    SystemInit();

    main();
    while (1);  // main must not return
}
```

### FreeRTOS Task Shape

```c
static void comms_task(void *arg) {
    const TickType_t period = pdMS_TO_TICKS(100);
    TickType_t last = xTaskGetTickCount();

    for (;;) {
        // do periodic work
        if (process_inbox() != COMMS_OK) {
            log_error("comms inbox processing failed");
        }
        vTaskDelayUntil(&last, period);  // absolute, drift-free
    }
}

// creation
BaseType_t ok = xTaskCreate(
    comms_task,
    "comms",
    512,   // stack size in words (4 bytes each on Cortex-M) — measure, do not guess
    NULL,
    tskIDLE_PRIORITY + 2,
    NULL);
configASSERT(ok == pdPASS);
```

### Interrupt-Safe Ring Buffer (lock-free, single producer / single consumer)

```c
typedef struct {
    volatile uint32_t head;
    volatile uint32_t tail;
    uint8_t buf[256];  // size must be power of 2
} rb_t;

// producer (ISR)
bool rb_push_isr(rb_t *rb, uint8_t b) {
    uint32_t next = (rb->head + 1) & 0xFF;
    if (next == rb->tail) return false;  // full
    rb->buf[rb->head] = b;
    __DMB();  // memory barrier — ensure data visible before head advance
    rb->head = next;
    return true;
}

// consumer (task)
bool rb_pop(rb_t *rb, uint8_t *out) {
    if (rb->tail == rb->head) return false;  // empty
    *out = rb->buf[rb->tail];
    __DMB();
    rb->tail = (rb->tail + 1) & 0xFF;
    return true;
}
```

## Debugging Toolkit
- **SWD/JTAG probe**: J-Link, ST-Link, Black Magic Probe, CMSIS-DAP
- **Debugger**: GDB + OpenOCD / pyOCD, or vendor IDE
- **Logic analyzer**: Saleae, DSLogic for protocol decode
- **Oscilloscope**: for timing, signal integrity, current measurement
- **RTT (Real-Time Transfer)**: SEGGER RTT for log output without UART bandwidth
- **SystemView / Tracealyzer**: RTOS task timing visualization

## Reference Links to Verify
- Chip reference manual (primary source — not the datasheet summary)
- Errata sheet (critical — half of "chip bugs" are documented)
- CMSIS documentation for the Cortex-M core in use
- FreeRTOS or Zephyr official docs for the RTOS version in use
