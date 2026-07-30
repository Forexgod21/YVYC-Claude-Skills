# Embedded Systems Expert — How To Use

**Skill:** `embedded-systems`
**Category:** Dev
**Author:** YourVisionYourCreation LLC
**License:** CC BY 4.0

---

## What This Skill Does

Embedded Systems Expert makes Claude write firmware like someone who has
actually bricked a board and learned from it — ARM Cortex-M, ESP32, STM32,
nRF, RP2040, FreeRTOS and Zephyr, bare-metal, interrupt discipline, DMA
cache maintenance, linker scripts, peripheral bringup order, and the
debugging toolkit (SWD, logic analyzer, oscilloscope, RTT) that goes with
all of it.

---

## The Problem It Solves

Embedded is the domain where generic AI code advice is most dangerous,
because the failures are silent, hardware-dependent, and expensive to
find. `printf` in an ISR. Missing D-cache invalidation before a DMA read.
A forgotten peripheral clock enable producing a HardFault that looks like
anything but a clock problem. This skill carries the discipline that
prevents them:

- ISR rules: short, deterministic, no malloc, no printf, no unguarded
  floating-point
- DMA cache maintenance rules for Cortex-M7 spelled out per direction
- Peripheral bringup in the order that actually works (clock first)
- A ten-row HardFault-and-friends symptom table mapped to root causes
- Verification gates: measured stack usage, ISR timing on a scope, `.map`
  file review before merge

---

## Quick Start

```
Bring up SPI on this STM32 — full init sequence with status checks.
```
```
HardFault on boot, PC is garbage. Walk the diagnosis.
```
```
Design the FreeRTOS task structure for this sensor node: sampling,
comms, and power budget.
```
```
Write an interrupt-safe ring buffer between my UART ISR and the
processing task.
```

---

## Key Disciplines

| Area | The Rule |
|---|---|
| ISRs | Short, non-blocking, no allocation, no printf — defer real work to tasks |
| DMA on M7 | Invalidate cache before DMA reads, clean after CPU writes, align to 32 bytes |
| Bringup order | Clock → GPIO alt function → peripheral config → NVIC → enable |
| Shared state | `volatile` AND a critical section or lock-free primitive — one alone is a bug |
| Stack sizes | Measured with watermarks and `-fstack-usage` — never guessed |
| Shipping | Watchdog fed from the main loop, brownout enabled, recoverable bootloader |

---

## What This Skill Will Not Do

- Put `printf`, malloc, or unguarded floats inside an ISR
- Guess a stack size instead of measuring one
- Trust the datasheet summary over the reference manual and errata sheet
- Ship firmware with no watchdog or no recovery path from a bad image

---

## Installation

1. Copy the `SKILL.md` file from this folder
2. Place it in your Claude skills directory
3. Install `shared-kernel` (from `agentic/`) alongside it — this skill
   loads it first
4. It activates automatically on any firmware, MCU, RTOS, ISR, or
   hardware-bringup task

---

*Part of the YVYC Claude Skills Library — Dev Category*
*YourVisionYourCreation LLC — [yourvisionyourcreation.com](https://www.yourvisionyourcreation.com)*
*Licensed under CC BY 4.0 — Free to use with attribution to YourVisionYourCreation LLC*
