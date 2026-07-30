---
name: debugging-wizard
category: dev
description: Use for diagnosing bugs, crashes, memory leaks, race conditions, deadlocks, performance regressions, production incidents, and flaky tests — stack trace analysis, core dump inspection, heap profiling, flame graphs, distributed tracing, log correlation, reproducing intermittent failures, bisecting regressions via git bisect, and root-cause analysis. Triggers on mentions of bug, crash, leak, slow, flaky, hang, deadlock, segfault, OOM, stack trace, panic, exception, "why is this broken", "what's wrong with", or any diagnostic framing.
---

# Debugging Wizard

## Load Order
Read `shared-kernel/SKILL.md` first.

## Core Principle
**Do not guess. Reproduce, observe, hypothesize, falsify, fix, verify.**

Debugging is applied epistemology. Every shortcut is a debt the next bug collects.

## Debugging Protocol

### Phase 1 — Reproduce
You do not have a bug until you can trigger it on demand.
1. Capture the exact input that produced the failure
2. Capture the environment: OS, runtime version, library versions, env vars
3. Capture the observable: error message (full, not summary), stack trace, logs, screenshot
4. Build the smallest script or test that reliably reproduces

If the bug is intermittent:
- Run the reproduction 100 times and measure the failure rate
- Capture all artifacts from every run, not just failures
- Look for shared state: caches, connection pools, file handles, environment

### Phase 2 — Observe
Read the evidence you have. Do not theorize past it.
- Full stack trace, top to bottom — the framework frames matter as much as your frames
- Full error message, including nested `cause` chains
- Logs from ±5 seconds around the failure
- Metrics from the same window — CPU, memory, GC, connection count

### Phase 3 — Hypothesize
Form the **cheapest falsifiable hypothesis** first.
- "It fails because X" → what would prove X wrong in under 5 minutes?
- Run that test before anything bigger
- If X is falsified, move to the next hypothesis — do not try to salvage X

### Phase 4 — Bisect
When a known-good version exists:

```bash
git bisect start
git bisect bad HEAD
git bisect good v1.2.3
git bisect run ./reproduce.sh   # script exits 0 if good, non-zero if bad
```

Bisect collapses "somewhere in 400 commits" to "this one commit" in log₂(n) steps.

### Phase 5 — Instrument
If observation is insufficient, add signal:
- Structured logs at every decision point in the code path
- Tracepoints at function entry/exit with arguments and return values
- `perf` / `dtrace` / `eBPF` / `py-spy` for sampling profiles
- `strace` / `dtruss` for syscall-level observation
- Wireshark / tcpdump for network-level observation

### Phase 6 — Fix Root Cause
Not the symptom. The cause.
- If a null pointer crashed the service, do not wrap it in a null check and move on — find why it was null.
- If a test is flaky, do not add `retry(3)` — find why it is flaky.
- If a deploy failed, do not `kubectl delete pod` — find why it failed.

### Phase 7 — Verify
- Add a regression test that fails before the fix and passes after
- Deploy the fix to staging, reproduce the original trigger, confirm the failure does not recur
- Monitor production metrics for 24 hours after the fix lands

## Diagnostic Tool Matrix

| Symptom | First Tool | Second Tool |
|---|---|---|
| High CPU | Sampling profiler (`perf`, Instruments, `py-spy`, `async-profiler`) | Flame graph |
| Memory leak | Heap profiler (Instruments, `pprof`, `valgrind`, Chrome DevTools) | Heap diff between two snapshots |
| Deadlock | Thread dump (`jstack`, `py-spy dump`, lldb `thread backtrace all`) | Lock graph analysis |
| Slow DB query | `EXPLAIN ANALYZE` | `pg_stat_statements` / slow query log |
| Flaky test | Run 100×, capture artifacts | Check shared state, test isolation, race conditions |
| Network issue | `tcpdump` / Wireshark | mtr / traceroute + timestamp correlation |
| Crash / segfault | Core dump + debugger (`gdb`, `lldb`) | ASAN / UBSAN / valgrind |
| OOM kill | Container memory limit vs actual usage | Heap profile at time of kill |
| Race condition | ThreadSanitizer (TSAN) | Deterministic replay (rr, Pernosco) |
| Intermittent 500s | Log correlation by request ID | Distributed trace by trace ID |

## Common Failure Signatures

### "It works on my machine"
- Environment variable present locally, missing in CI
- File in local checkout, missing from container image
- Different OS path separator (`\` vs `/`)
- Different locale / timezone / encoding
- Different library version

### "It works the first time"
- Caching masking subsequent failures
- Connection pool exhausted after N requests
- File handle leak reaching ulimit
- Token expiration

### "It works in isolation but fails under load"
- Connection pool too small
- Lock contention
- GC pressure under allocation rate
- Thread pool starvation

### "It used to work"
- Dependency auto-upgraded (check lockfile)
- Data changed shape (schema migration, new edge case)
- Infrastructure changed (certificate rotation, DNS change, IAM change)
- `git bisect` is the answer

## Non-Negotiables
- Do not fix what you cannot reproduce
- Do not ship the fix without a regression test
- Do not close the ticket until root cause is documented
- State the root cause in the postmortem, not the symptom that went away
- If the fix is "I restarted the service," the investigation is not done

## Anti-Patterns to Refuse

| Anti-Pattern | Why It Fails |
|---|---|
| `except: pass` | Swallows the signal you need |
| `retry(100)` on flaky test | Hides the race, does not fix it |
| `sleep(5)` to "let things settle" | Masks timing bug that will return |
| Commenting out failing assertion | The assertion was correct; the code is wrong |
| `// TODO: figure out why` merged to main | Investigation debt compounds |
| "Works now, must have been a fluke" | Heisenbugs do not self-heal |

## Postmortem Template (for production incidents)

```
INCIDENT: [short name]
DATE: [UTC]
DURATION: [detection to mitigation]
IMPACT: [users affected, revenue, SLO burn]

TIMELINE:
  HH:MM — event
  HH:MM — event

ROOT CAUSE:
  [the actual cause, not the trigger]

CONTRIBUTING FACTORS:
  - [what made it worse or delayed detection]

RESOLUTION:
  [what was done to stop the bleeding]

ACTION ITEMS:
  - [owner] [action] [due date]

LESSONS LEARNED:
  [what the team now knows]
```

## Reference Links to Verify
- https://brendangregg.com/ (performance and systems debugging)
- https://sre.google/workbook/postmortem-culture/ (blameless postmortem doctrine)
- Platform-specific: Apple Instruments docs, Linux perf wiki, Chrome DevTools docs
