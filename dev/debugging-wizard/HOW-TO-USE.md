# Debugging Wizard — How To Use

**Skill:** `debugging-wizard`
**Category:** Dev
**Author:** YourVisionYourCreation LLC
**License:** CC BY 4.0

---

## What This Skill Does

Debugging Wizard replaces guess-and-check debugging with a seven-phase
protocol: reproduce, observe, hypothesize, bisect, instrument, fix the
root cause, verify. It covers crashes, leaks, deadlocks, race conditions,
performance regressions, flaky tests, and production incidents — with a
symptom-to-tool matrix so the right profiler, tracer, or debugger gets
reached for first, not fifth.

The core principle in one line: **do not guess — reproduce, observe,
hypothesize, falsify, fix, verify.**

---

## The Problem It Solves

Default debugging behavior — human and AI alike — is symptom-patching:
wrap the null in a null check, add `retry(3)` to the flaky test, restart
the service and call it fixed. Every one of those collects debt the next
bug cashes in. This skill makes the shortcuts impossible:

- No fix without a reproduction
- No shipped fix without a regression test that fails before and passes
  after
- No closed ticket without a documented root cause
- "I restarted the service" is explicitly not a completed investigation

---

## Quick Start

```
This service crashes intermittently under load — here's the stack trace
and logs. Diagnose it.
```
```
This test passes alone but fails in CI about 20% of the time.
```
```
It worked last week. 400 commits since. Find the regression.
```
```
Memory climbs 50MB an hour until the container gets OOM-killed.
```

---

## The Seven Phases

| Phase | What Happens |
|---|---|
| 1. Reproduce | No bug exists until it triggers on demand — smallest reliable repro first |
| 2. Observe | Read the full evidence: complete traces, cause chains, ±5s of logs and metrics |
| 3. Hypothesize | Cheapest falsifiable hypothesis first — test it in under 5 minutes |
| 4. Bisect | `git bisect run` collapses 400 commits to one in log₂(n) steps |
| 5. Instrument | Add signal when observation runs dry: profilers, tracepoints, packet capture |
| 6. Fix root cause | The reason it was null — not a null check over the symptom |
| 7. Verify | Regression test, staging reproduction, 24 hours of production metrics |

---

## The Tool Matrix

Ten symptoms mapped to their first and second diagnostic tool — high CPU
to flame graphs, deadlocks to thread dumps, flaky tests to 100-run
artifact capture, intermittent 500s to trace-ID correlation. Plus the four
classic failure signatures decoded: "works on my machine," "works the
first time," "works in isolation," and "used to work."

---

## What This Skill Will Refuse

- `except: pass` and its cousins — swallowing the signal you need
- Retry wrappers and `sleep(5)` as fixes for timing bugs
- Commenting out the failing assertion
- Closing an incident with the symptom named instead of the cause

---

## Installation

1. Copy the `SKILL.md` file from this folder
2. Place it in your Claude skills directory
3. Install `shared-kernel` (from `agentic/`) alongside it — this skill
   loads it first
4. It activates automatically on any bug, crash, leak, perf, or "why is
   this broken" framing

---

*Part of the YVYC Claude Skills Library — Dev Category*
*YourVisionYourCreation LLC — [yourvisionyourcreation.com](https://www.yourvisionyourcreation.com)*
*Licensed under CC BY 4.0 — Free to use with attribution to YourVisionYourCreation LLC*
