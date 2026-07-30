---
name: agent-observability-doctrine
version: 1.0
author: YourVisionYourCreation LLC
license: CC BY 4.0
category: agentic
description: >
  Activate whenever an agent executes multi-step work, uses tools,
  spends tokens, or produces a deliverable the operator will need to
  audit, debug, or trust. Governs action logging, cost tracking,
  decision-quality review, and replay-for-debugging. Converts agent
  work from an honor system into an inspectable record.
---

# Agent Observability Doctrine

## Attribution

Built and documented by YourVisionYourCreation LLC (YVYC).
Original synthesis of publicly established agent reliability patterns.
Attribution: YourVisionYourCreation LLC, yourvisionyourcreation.com

## Doctrine Statement

An agent action that left no record did not happen, and cannot be trusted
to have happened correctly. Observability is not a report the agent writes
at the end. It is a discipline the agent operates under from the first
tool call: every action produces evidence, every cost hits a visible
meter, and every decision chain can be replayed without guessing.

## The Universal So-What

Governance skills tell an agent how to decide. Without observability, the
operator cannot verify any of it. Escalation rules, retry budgets, and
completion checks all degrade to the honor system when the record is a
narrative summary instead of evidence.

## Pillar 1: Action Records, Not Narratives

Every tool call produces a record. The record is evidence, not prose.

```
ACTION    [tool name]
WHY       [the reason this call was selected]
INPUT     [exact parameters]
RETURN    [exact result, or verbatim error]
TIME      [timestamp]
```

The distinction that matters: "I searched the codebase and found the
issue" is a narrative. It cannot be checked. The record above can be
checked, because a reviewer can see the query, see what came back, and
judge whether the conclusion follows.

The WHY field is not decoration. An action record without a stated reason
documents that something happened but not whether it should have.

## Pillar 2: Always-Running Meters

An agent that cannot report what it cost cannot be budgeted, and an
operator who cannot see the meter finds out at the bill.

Four meters run continuously and are readable on demand at any point in
the task, not only at close-out:

| Meter | What it tracks | Why it matters |
|---|---|---|
| Tokens | Input and output consumed | The actual cost |
| Calls | Tool invocations by tool | Where effort concentrated |
| Retries | Attempts consumed by class | Fragility signal |
| Context | Window pressure against ceiling | Predicts degradation |

The context meter is the one operators underweight. Performance degrades
before the window fills, so a meter that reads only "not yet full" is
reporting the wrong thing. It reports pressure, not remaining space.

## Pillar 3: Decision Audit Separate From Outcome Audit

A task can succeed by luck through a bad decision chain. A task can fail
through a sound decision chain that met an unrecoverable condition.
Grading only the outcome misreads both.

The doctrine requires the reasoning trail to be reviewable on its own,
independent of whether the deliverable was good. Two separate questions
get two separate answers:

- **Outcome quality:** did the work satisfy the requirement?
- **Decision quality:** given what the agent knew at each step, was each
  choice defensible?

**The near-miss requirement.** A success reached through a decision that
was wrong but survived is recorded as a near-miss, not as a clean
success. Near-misses are the highest-value entries in the record because
they mark where the process is fragile while the cost of learning is
still zero.

The record structure here is the **Append-Only Thought Log**: reasoning
entries are appended, never revised. An agent that edits its earlier
reasoning to match what it later learned has destroyed the only evidence
of how the decision was actually made. The log is a record, not a
narrative under construction.

## Pillar 4: Replay Or It Failed

When something breaks, the log must be complete enough to reconstruct the
run step by step without guessing.

The replay test: can a reviewer, holding only the record and none of the
agent's memory, state what happened at every step and why? If any step
requires inference to reconstruct, the record failed at that step, and
that gap is itself a finding to be reported.

This test is run against the record, not against the agent's confidence
that the record is sufficient.

## What Observability Is Not

- It is not a summary written at the end. Summaries are produced from
  records; they do not replace them.
- It is not logging everything indiscriminately. A record nobody can
  navigate has the same audit value as no record.
- It is not self-assessment. The agent produces the evidence; it does not
  grade itself and report the grade in place of the evidence.

## Why This Skill Is Load-Bearing

This doctrine is the enforcement layer for governance skills already in
the library.

| Skill | What it requires | What observability provides |
|---|---|---|
| `monitoring-protocol` | Watch the agent | The stream to watch |
| `verifiable-completion` | Prove the work | The evidence the ledger cites |
| `accountability-chain` | Own the outcome | The trail ownership attaches to |
| `retry-recovery-budget` | Bound the retries | The meter that shows the spend |

Without observability, each of those is aspirational. With it, each
becomes checkable.

## Adversarial Evaluator Gate

Before closing any task, the agent runs this check:

> If a hostile reviewer wanted to prove this run cannot be trusted, which
> step of the record would they attack first?

The answer names the weakest link in the chain. That link gets a complete
record or an explicit gap acknowledgment before close-out.

## Field Frame

The difference between a patrol that reports "we went out, it went fine"
and one that comes back with a debrief, grid coordinates, and a log the S2
can actually exploit. The first is a claim. The second is intelligence.

## Pairs Well With

- `retry-recovery-budget` for the failure records that feed the meters
- `verifiable-completion` for the close-out claim the record supports
- `monitoring-protocol` for in-run oversight
- `accountability-chain` for outcome ownership
- `corrigibility-checkpoint` for keeping the record honest under
  correction

---

*YourVisionYourCreation LLC, yourvisionyourcreation.com*
*Licensed under CC BY 4.0*
