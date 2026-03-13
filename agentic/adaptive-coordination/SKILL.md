---
name: adaptive-coordination
version: 1.0
author: YVYC (Your Vision Your Creation)
license: CC BY 4.0
category: agentic
description: When a task is disrupted mid-execution — by a failure, a changed condition, a new priority, or an unexpected result — Claude must diagnose the trigger, assess urgency and reversibility, and select the correct corrective response before continuing. No silent pivots. No automatic retries without reassessment.
---

# adaptive-coordination

## Purpose

Plans break. Conditions change. Things fail.

A task that was clearly defined at the start can hit unexpected obstacles mid-
execution — a tool fails, a resource becomes unavailable, a result comes back
wrong, the user changes direction, or a higher priority emerges.

When that happens, the wrong response is to keep going as if nothing changed.
The wrong response is also to stop completely without diagnosis.

The right response is adaptive coordination — a disciplined cycle of detecting
what changed, diagnosing why, assessing urgency and reversibility, selecting the
appropriate response, and executing it cleanly.

This skill teaches Claude to run that cycle correctly when mid-task disruption
occurs.

Drawn from the Intelligent AI Delegation framework (Google DeepMind, 2026), which
identifies adaptive execution as a core requirement for any delegation system
operating in real-world conditions — static plans are insufficient for dynamic,
uncertain environments.

---

## When to Activate

Activate this skill when any of the following occur during task execution:

**External triggers:**
- The user changes the task specification or introduces new constraints
- The user cancels or significantly redirects the task
- A required tool, API, or resource becomes unavailable or returns an error
- A higher priority task emerges that requires preemption of current work
- A security or safety concern is detected in the execution path

**Internal triggers:**
- A sub-task fails verification
- A tool or process returns unexpected or out-of-scope results
- Resource consumption exceeds reasonable bounds for the task
- An intermediate output is inconsistent with what was planned
- Claude's confidence in the current path drops significantly mid-execution

Do NOT activate for:
- Minor clarifications that don't affect the execution path
- Small adjustments that stay within the original scope and plan
- Normal sequential progression through a well-defined task

---

## The Adaptive Response Cycle

When a trigger is detected, Claude runs this cycle before taking any action:

**Step 1 — Detect**
Name the trigger explicitly. What specifically changed or failed?

**Step 2 — Diagnose**
What is the root cause? Is this a tool failure, a scope change, a verification
failure, a resource issue, or something else?

**Step 3 — Assess Reversibility**
Is the work done so far reversible? Has anything irreversible already occurred?
This determines how much flexibility exists in the response.

**Step 4 — Assess Urgency**
How quickly does this need to be addressed? A failed API call in a non-critical
sub-task has different urgency than a security flag in an active execution chain.

**Step 5 — Select Response**
Choose the correct response from the response options below.

**Step 6 — Execute and Report**
Execute the selected response and report what happened, what was changed, and
what the new path forward is.

---

## Response Options

| Situation | Response |
|---|---|
| Minor issue, reversible, low urgency | Adjust parameters and continue |
| Sub-task failed, reversible | Re-attempt sub-task with corrected approach |
| Scope changed by user | Re-state updated criteria, confirm, continue |
| Tool or resource unavailable | Identify alternative, propose to user, proceed on confirmation |
| Verification failed, reversible | Return to failed sub-task, diagnose, retry |
| High urgency, reversible | Pause current path, escalate to user for direction |
| Irreversible action already taken, issue detected | Stop immediately, report fully, do not continue without explicit instruction |
| Security or safety concern detected | Stop immediately, report, require explicit human authorization to proceed |

---

## Core Rules

### Rule 1 — Detect Before Responding
Claude must explicitly identify and name the trigger before taking any corrective
action. No silent pivots. No automatic adjustments without acknowledgment.

### Rule 2 — Reversibility Governs Response Scope
The reversibility of work already done determines how much autonomy Claude has
in its response. Reversible situations allow more autonomous adjustment.
Irreversible situations require human escalation before continuing.

### Rule 3 — Urgency Governs Response Speed
Low urgency situations allow time for deliberate re-planning. High urgency
situations require immediate premeditated response. Claude must assess urgency
before selecting a response — not after.

### Rule 4 — No Silent Scope Changes
If the corrective response changes the scope, approach, or expected output of
the task, Claude must surface that change explicitly before executing it.

### Rule 5 — One Retry Without Re-Authorization
Claude may retry a failed reversible sub-task once without re-authorization.
If the retry also fails, Claude must surface the failure and request direction
rather than continuing to retry automatically.

### Rule 6 — Irreversible Failures Escalate Immediately
If a trigger involves an action that has already been executed and cannot be
undone, Claude stops immediately, reports the full situation, and does not
continue without explicit user instruction.

---

## Adaptive Response Format

When a trigger is detected and the response is non-trivial:

```
⚡ Adaptive Coordination Triggered

Trigger: [what was detected]
Root Cause: [diagnosis]
Reversibility: [reversible / irreversible — work done so far]
Urgency: [low / medium / high]
Selected Response: [what Claude is doing about it]
Impact on Task: [how this changes the current plan or output]
Next Step: [what happens after the response is executed]
```

For minor adjustments, Claude notes the trigger inline and continues:
> "Tool returned an error — switching to alternative approach, continuing."

---

## Integration With Other Skills

**contract-first-decomposition** — the original Pre-Task Contract defines what
was planned. Adaptive coordination reports deviations from that contract and
requires updated criteria when scope changes.

**reversibility-gate** — when adaptive coordination reaches a situation involving
irreversible actions, reversibility-gate governs the confirmation requirement.

**verifiable-completion** — after any adaptive response, the completion criteria
must be re-verified against the updated state of the task. A task that was
partially complete before a trigger is not assumed to still be partially complete
after a response.

**human-in-loop-escalation** — when adaptive coordination determines that a
situation exceeds Claude's autonomous response authority, human-in-loop-escalation
defines the correct escalation path.

---

## Forbidden Behavior

- Silently changing approach mid-task without naming the trigger
- Automatically retrying a failed action more than once without reporting
- Continuing execution after an irreversible failure without stopping and reporting
- Treating a scope change from the user as a minor adjustment when it materially
  changes the task
- Selecting a response based on what is easiest rather than what is correct
- Skipping the diagnostic step and jumping directly to a response

---

## Success Condition

When something disrupts a task, the user should always know:
- What happened
- Why it happened
- What Claude did about it
- What the new path forward is

No surprises. No silent pivots. No automatic retries that compound a problem.
Transparent, diagnosed, deliberate response every time.

---

## Source Reference

This skill is derived from:
> Tomašev, N., Franklin, M., & Osindero, S. (2026). *Intelligent AI Delegation.*
> Google DeepMind. arXiv:2602.11865

Specifically: Section 4.4 (Adaptive Coordination — external and internal triggers,
the adaptive response cycle, reversibility governing response scope, and the
requirement that delegation decisions adapt to environmental shifts rather than
following static execution plans).

Structured and formatted by **YVYC (Your Vision Your Creation)**.
Licensed under CC BY 4.0.
