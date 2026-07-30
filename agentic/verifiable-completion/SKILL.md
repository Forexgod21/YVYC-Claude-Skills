---
name: verifiable-completion
version: 1.0
author: YourVisionYourCreation LLC
license: CC BY 4.0
category: agentic
tier: 2
description: >
  Activate whenever an agent is about to report a task as done, finished,
  complete, ready, or shipped. Governs what evidence must exist before a
  completion claim is permitted, how partial completion is reported, and
  what an agent must never assert without verification. Prevents the
  single most damaging agent failure mode: confident completion claims
  for work that was never verified.
---

# Verifiable Completion

## Attribution

Structured, translated, and built by YourVisionYourCreation LLC (YVYC).

Research foundation: Tomasev, N., Franklin, M., and Osindero, S. (2026).
*Intelligent AI Delegation.* Google DeepMind. arXiv:2602.11865, on
completion verification and the delegation trust gap.

Attribution: YourVisionYourCreation LLC, yourvisionyourcreation.com

## Doctrine Statement

"Done" is a claim about reality, not a feeling about effort. An agent
that reports completion without evidence has not finished the task. It
has finished working on the task, which is a different event, and
reporting the second as the first is how delegation breaks.

The core rule: no completion claim without a completion check the
operator could run themselves and get the same answer.

## The Universal So-What

Delegation collapses at exactly one point: the operator stops being able
to trust "done." Once an agent has reported success on work that was
broken, every future report requires manual re-verification, which
erases the entire value of delegating. This skill protects the one asset
the delegation relationship cannot survive losing.

## The Completion Ledger

Before any completion claim, the agent produces a ledger with four
columns. The ledger is not optional and is not a narrative.

| Requirement | Evidence | Verified by | State |
|---|---|---|---|
| What was asked | What proves it happened | The check that was run | MET / PARTIAL / NOT MET |

Rules for the ledger:

- Every requirement from the original task appears as its own row.
  Requirements are not merged, summarized, or inferred away.
- Evidence is an artifact: a command output, a file path, a test result,
  a returned value. Evidence is never the agent's own assertion.
- "Verified by" names the check performed. If no check was performed,
  the cell reads NOT VERIFIED and the state cannot be MET.
- A single NOT MET row makes the whole task incomplete. There is no
  averaging.

## The Three Permitted Reports

An agent finishing work may return exactly one of three reports. No
fourth option exists.

**1. COMPLETE.** Every requirement is MET with evidence and a named
check. The ledger is attached.

**2. PARTIAL.** One or more requirements are PARTIAL or NOT MET. The
report leads with what is missing, not with what was accomplished. The
agent states what remains, what blocked it, and one recommended next
action.

**3. BLOCKED.** Work could not proceed. The agent reports the blocker
verbatim, what was attempted, and what it needs from the operator.

Reporting COMPLETE when the ledger contains an unverified row is the
failure this skill exists to make impossible.

## Verification Tiers

Not all evidence carries the same weight. The agent selects the highest
tier available and records which tier it used.

| Tier | Evidence type | Trust |
|---|---|---|
| 1 | Independent check that would fail if the work were wrong | Highest |
| 2 | Direct observation of the changed state | High |
| 3 | Tool return value reporting success | Moderate |
| 4 | Absence of an error message | Low |
| 5 | The agent's recollection of having done it | None |

Tier 4 alone never supports a COMPLETE report. Nothing failing is not
the same as something working. Tier 5 is not evidence and is never
recorded as such.

## Prohibited Completion Language

The agent does not use these constructions in a completion report:

- "Should be working now" (prediction, not verification)
- "Should be all set" (same failure, softer)
- "I've made the changes" as a standalone claim (action, not outcome)
- "Everything looks good" without naming what was inspected and how
- "Fixed" without the check that proves the original failure is gone

Each of these transfers verification burden back to the operator while
sounding like it removed it.

## The Regression Check

A completion claim on a fix carries one added requirement: the agent must
confirm the original failure no longer reproduces, using the same
conditions that produced it. A fix verified only by the absence of new
errors is a Tier 4 claim wearing a Tier 1 uniform.

## Partial Completion Discipline

Partial work is a legitimate outcome and is reported without softening.

- Lead with the gap. The operator needs the delta first, not a summary
  of effort.
- Preserve all completed work in a recoverable state. Partial completion
  never means partial destruction.
- State the next action as one recommendation, not a menu.
- Never round a PARTIAL up to COMPLETE because the remaining work looks
  minor. Minor to the agent is unknown to the operator.

## Interaction With Escalation

When verification is impossible inside the agent's authority, for
instance when the only true check requires a permission the agent does
not hold, the agent does not substitute a weaker tier and proceed. It
reports the ceiling it hit and escalates. This is the JumpMaster Rule
applied to verification: a gray area in the evidence goes up, never
resolved quietly at the agent's level.

## Adversarial Evaluator Gate

Before any completion report leaves the agent, it runs this check:

> If a hostile reviewer took this report and tried to prove the work was
> not actually done, where would they attack first?

The answer names the weakest row in the ledger. That row gets a stronger
check or an honest downgrade before the report ships. A report that
cannot survive this question is not ready to send.

## Failure Modes This Skill Closes

| Failure mode | What it looks like | What this skill requires instead |
|---|---|---|
| Effort as outcome | "I worked through all the files" | Named artifact per requirement |
| Silent partial | Success report omitting a skipped step | Every requirement gets a row |
| Error-absence proof | "No errors, so it works" | A check that would fail if broken |
| Requirement drift | Reporting on a task adjacent to the one asked | Requirements copied from the original ask |
| Optimistic rounding | Calling 90 percent done | PARTIAL with the gap stated first |

## Pairs Well With

- `retry-recovery-budget` to confirm no failed step was silently skipped
  before close-out
- `agent-observability-doctrine` for the record structure the ledger
  writes into
- `human-in-loop-escalation` for the handoff when verification exceeds
  agent authority
- `accountability-chain` for who owns a completion claim once it is made
- `monitoring-protocol` for verification during the run rather than only
  at the end

---

*YourVisionYourCreation LLC, yourvisionyourcreation.com*
*Licensed under CC BY 4.0*
