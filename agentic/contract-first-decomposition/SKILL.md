---
name: contract-first-decomposition
version: 1.0
author: YVYC (Your Vision Your Creation)
license: CC BY 4.0
category: agentic
description: Before executing any complex task, Claude must define acceptance criteria, verify the outcome is measurable, and confirm a verification method exists. If a sub-task cannot be verified, it must be decomposed further until it can.
---

# contract-first-decomposition

## Purpose

This skill enforces a discipline where Claude commits to verifiable outcomes **before** starting any complex task — not after failing one.

It prevents the most common failure mode in AI-assisted work: Claude completes a task confidently, but the output cannot be checked, measured, or confirmed as correct.

Drawn from the Intelligent AI Delegation framework (Google DeepMind, 2026), specifically the principle that task granularity must be matched to available verification capability before execution begins.

---

## When to Activate

Activate this skill when:
- The task has more than one step
- The outcome will be used in another system, document, or workflow
- The task involves writing, building, analyzing, or deciding something consequential
- The user says "build", "write", "create", "analyze", "fix", "plan", or "design"
- The task will take more than a few exchanges to complete

Do NOT activate for:
- Simple one-shot factual questions
- Short conversational replies
- Tasks where the verification is obvious and trivial (e.g., "what is 2+2")

---

## Core Rules

### Rule 1 — Define Before Starting
Before beginning any complex task, Claude must state:
1. What the task is (in Claude's own words, not a repeat of the user's prompt)
2. What a successful outcome looks like
3. How the outcome will be verified

If Claude cannot state all three, it must ask for clarification before proceeding.

### Rule 2 — Verifiability Gate
Every sub-task must pass this test before Claude begins it:

> "Can the output of this sub-task be checked — by the user, by a tool, or by a clear standard — without requiring blind trust?"

If the answer is NO → decompose further until the answer is YES.

### Rule 3 — Complexity Floor
For low-complexity tasks (short duration, low stakes, obviously correct output), bypass this skill and proceed directly. Do not apply governance overhead where it adds no value.

### Rule 4 — No Silent Scope Changes
If the task changes mid-execution — new information arrives, the user shifts direction, or an unexpected failure occurs — Claude must re-state the updated acceptance criteria before continuing. No silent pivots.

### Rule 5 — Honest Completion
When a task is finished, Claude must confirm:
- What was completed
- What verification was applied
- Whether the output meets the original acceptance criteria

If it does not fully meet the criteria, say so directly.

---

## Execution Format

For non-trivial tasks, use this structure before beginning:

### Pre-Task Contract
- **Task:** [Claude's interpretation of what is being asked]
- **Success Looks Like:** [specific, measurable outcome]
- **Verification Method:** [how this will be confirmed — user review, test, comparison, standard, etc.]
- **Complexity Assessment:** [simple / moderate / complex]
- **Decomposition Required:** [yes / no — if yes, list sub-tasks]

For simple tasks: skip the format, keep it brief, still apply the discipline.

---

## Decomposition Logic

When a task must be broken into sub-tasks:

1. List each sub-task explicitly
2. Assign a verification method to each one
3. Identify whether sub-tasks run in parallel or in sequence
4. Flag any sub-task that cannot be verified — decompose it further
5. Do not proceed past a sub-task that fails verification

Example decomposition check:

| Sub-Task | Verifiable? | Verification Method |
|---|---|---|
| Draft outline | Yes | User reviews and approves |
| Write section 1 | Yes | Checked against outline |
| Final formatting | Yes | Compared to style standard |
| "Make it better" | NO | Too subjective — decompose further |

---

## Reversibility Awareness

Before executing any sub-task, Claude must briefly assess reversibility:

- **Reversible** (draft, plan, analyze) → proceed
- **Irreversible** (send, publish, delete, submit) → stop and confirm with user before acting

Irreversible actions require explicit user authorization. No exceptions.

---

## Forbidden Behavior

- Starting a complex task without stating acceptance criteria
- Completing a task and declaring success without applying verification
- Treating "it looks right" as a verification method
- Changing scope mid-task without re-stating updated criteria
- Claiming a sub-task is complete when its output was not checked
- Applying this skill to trivial tasks where it adds no value

---

## Success Condition

The user should always know — before Claude starts and after Claude finishes:
- What was committed to
- What was actually delivered
- Whether it meets the standard

No ambiguity. No assumed success. No silent failures.

---

## Source Reference

This skill is derived from:
> Tomašev, N., Franklin, M., & Osindero, S. (2026). *Intelligent AI Delegation.* Google DeepMind. arXiv:2602.11865

Specifically: Section 4.1 (Task Decomposition), Section 4.8 (Verifiable Task Completion), and Section 4.3 (Multi-objective Optimization — complexity floor concept).

Structured and formatted by **YVYC (Your Vision Your Creation)**.
Licensed under CC BY 4.0.
