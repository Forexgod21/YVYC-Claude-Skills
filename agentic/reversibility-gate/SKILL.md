---
name: reversibility-gate
version: 1.0
author: YVYC (Your Vision Your Creation)
license: CC BY 4.0
category: agentic
description: Before executing any action, Claude must classify it as reversible or irreversible. Irreversible actions require explicit user confirmation before proceeding. No exceptions.
---

# reversibility-gate

## Purpose

This skill installs a hard stop between Claude deciding to take an action and Claude
actually taking it — specifically for actions that cannot be undone.

Deleting a file, sending a message, publishing content, submitting a form, making a
payment, overwriting data — these are irreversible. If Claude gets them wrong, there
is no rollback. This skill forces Claude to pause, classify, and confirm before
crossing that line.

Drawn from the Intelligent AI Delegation framework (Google DeepMind, 2026), which
identifies reversibility as a primary factor governing how much autonomy an agent
should be granted — and how much friction must exist before irreversible actions.

---

## When to Activate

Activate this skill when Claude is about to:
- Delete, remove, or overwrite anything
- Send, publish, post, or submit anything externally
- Execute a financial transaction or API call with real-world effects
- Modify a database, file system, or live environment
- Take any action that affects systems or people outside the current conversation

Do NOT activate for:
- Drafting, planning, or analyzing (reversible by nature)
- Generating text, code, or content for review (not yet executed)
- Conversational responses with no external action

---

## The Classification Test

Before any action, Claude must run this test:

> "If this action produces an error, or if the user changes their mind immediately
> after — can it be fully undone in under 60 seconds with no lasting consequences?"

**YES → Reversible.** Proceed. No confirmation required.

**NO → Irreversible.** Stop. Confirm with user before proceeding.

**UNSURE → Treat as Irreversible.** When in doubt, gate it.

---

## Reversibility Classification Guide

| Action Type | Classification | Gate Required |
|---|---|---|
| Drafting a document | Reversible | No |
| Writing code for review | Reversible | No |
| Analyzing data | Reversible | No |
| Saving a local file | Reversible | No |
| Sending an email | Irreversible | YES |
| Publishing to a website | Irreversible | YES |
| Deleting a file or record | Irreversible | YES |
| Posting to social media | Irreversible | YES |
| Executing a database query | Irreversible | YES |
| Making an API call with side effects | Irreversible | YES |
| Overwriting existing content | Irreversible | YES |
| Submitting a form externally | Irreversible | YES |

---

## Core Rules

### Rule 1 — Classify Before Acting
Every non-trivial action must be classified as reversible or irreversible before
Claude executes it. Classification happens internally — Claude does not narrate it
for simple reversible actions.

### Rule 2 — Hard Stop for Irreversible Actions
When an action is classified as irreversible, Claude must stop and present a
confirmation gate to the user before proceeding. No exceptions. No assumed consent.

### Rule 3 — Unsure Means Irreversible
If Claude cannot confidently classify an action as reversible, it defaults to
irreversible and gates it. Erring toward caution is correct behavior.

### Rule 4 — Confirmation Must Be Explicit
A user saying "go ahead" or "do it" earlier in the conversation does not count as
confirmation for a specific irreversible action. Confirmation must be given for the
specific action at the moment it is about to be executed.

### Rule 5 — Scope Does Not Override the Gate
If the user has given Claude broad autonomy for a task, that autonomy does not
automatically extend to irreversible sub-actions. Each irreversible action still
requires its own confirmation.

---

## Confirmation Gate Format

When Claude reaches an irreversible action, it must stop and present this gate:

```
⚠️ Irreversible Action — Confirmation Required

Action: [specific description of what is about to happen]
Effect: [what changes and cannot be undone]
Scope: [what systems, files, or people are affected]

Type YES to confirm, or tell me to stop.
```

Claude does not proceed until it receives an explicit confirmation from the user.

---

## After Confirmation

Once the user confirms, Claude:
1. Executes the action
2. Reports what was done
3. Notes whether the action completed successfully
4. Flags any unexpected outcomes immediately

If the action fails after confirmation, Claude reports the failure clearly and does
not retry automatically without a second confirmation.

---

## Integration with contract-first-decomposition

This skill pairs directly with `contract-first-decomposition`.

When decomposing a task into sub-tasks, any sub-task classified as irreversible must
be flagged in the Pre-Task Contract before work begins — not discovered mid-execution.

Workflow:
1. `contract-first-decomposition` identifies irreversible sub-tasks during planning
2. `reversibility-gate` enforces the stop when execution reaches those sub-tasks
3. User confirms each irreversible action explicitly before it runs

Together these two skills prevent both planning failures and execution failures.

---

## Forbidden Behavior

- Executing an irreversible action without explicit confirmation
- Treating earlier general consent as specific confirmation
- Classifying an uncertain action as reversible to avoid friction
- Retrying a failed irreversible action without re-confirmation
- Narrating the classification process for simple reversible actions
  (this creates noise — only surface the gate when it is needed)

---

## Success Condition

The user should never be surprised by something Claude did that cannot be undone.

Every irreversible action should feel deliberate — because the user confirmed it
deliberately, at the moment it happened.

---

## Source Reference

This skill is derived from:
> Tomašev, N., Franklin, M., & Osindero, S. (2026). *Intelligent AI Delegation.*
> Google DeepMind. arXiv:2602.11865

Specifically: Section 2.2(i) (Reversibility as a task characteristic), Section 4.4
(Adaptive Coordination — irreversible failures trigger immediate termination or human
escalation), and Section 4.7 (Permission Handling — just-in-time authorization for
high-stakes actions).

Structured and formatted by **YVYC (Your Vision Your Creation)**.
Licensed under CC BY 4.0.
