# How To Use: Agent Observability Doctrine

**Category:** `agentic/` | **YVYC Original**

## What This Skill Does

It makes an agent's work inspectable. Every tool call leaves evidence,
every cost sits on a visible meter, the reasoning trail is auditable on
its own, and any failure can be replayed from the record without
guessing.

## Who This Is For

- Operators running agentic workflows they need to audit afterward
- Developers debugging agent behavior across long multi-step runs
- Anyone who has been handed a confident agent summary and had no way to
  check it
- Teams that need a cost trail, not a surprise bill

## Installation

1. Copy the `agent-observability-doctrine` folder into your Claude skills
   directory.
2. Confirm both files are present: `SKILL.md` and `HOW-TO-USE.md`.
3. The skill activates automatically whenever the agent runs multi-step
   work, uses tools, or produces an auditable deliverable.

## What Changes in Practice

**Before this skill:**
The agent works for twenty minutes and hands you a paragraph: "I reviewed
the codebase, found the root cause in the auth module, and applied a fix."
You cannot tell what it looked at, what it ruled out, what it cost, or
whether the reasoning held.

**After this skill:**
You get the action records for every call with inputs and returns, a meter
reading for tokens and calls and context pressure, a reasoning trail you
can grade separately from the result, and a record complete enough to
replay the whole run step by step.

## The Four Pillars

**1. Action records, not narratives.**
Each tool call logs what was called, why it was selected, the exact
inputs, and the exact return. "I searched and found the issue" is a
narrative you cannot check. A record you can.

**2. Always-running meters.**
Four meters you can read at any point in the run, not only at the end:

| Meter | Reads |
|---|---|
| Tokens | Input and output consumed |
| Calls | Invocations by tool |
| Retries | Attempts by failure class |
| Context | Window pressure against the ceiling |

Watch the context meter. Performance degrades before the window fills, so
a meter reporting "not yet full" is answering the wrong question.

**3. Decision audit separate from outcome audit.**
Two grades, not one. Did the work satisfy the requirement, and given what
the agent knew at each step, was each choice defensible? A task can
succeed by luck through bad decisions, and that gets flagged as a
**near-miss** rather than reported as a clean win. Near-misses are the
most useful entries you will get, because they mark fragility while it
still costs nothing to learn.

The reasoning record is **append-only**. The agent does not go back and
revise earlier reasoning to match what it learned later. If it did, you
would lose the only evidence of how the decision was actually made.

**4. Replay or it failed.**
The test: can someone holding only the record, with no access to the
agent's memory, reconstruct every step and the reason for it? If any step
needs inference to reconstruct, the record failed there, and the agent
reports that gap as a finding.

## Asking for the Meters Mid-Run

You can pull a reading at any time:

```
Meter check.
```

You get tokens, calls, retries by class, and context pressure, without
interrupting the work.

## What This Skill Will Not Give You

- A narrative summary in place of evidence. Summaries get produced from
  records; they do not substitute for them.
- Indiscriminate logging. A record nobody can navigate audits the same as
  no record.
- Self-grading. The agent produces evidence. It does not hand you its own
  performance review instead.

## Why It Makes Your Other Skills Real

| Skill you already run | What this adds |
|---|---|
| `monitoring-protocol` | The stream there is to watch |
| `verifiable-completion` | The evidence the completion ledger cites |
| `accountability-chain` | The trail ownership attaches to |
| `retry-recovery-budget` | The meter showing what the retries cost |

Without observability, all four run on the honor system.

## Pairs Well With

- `retry-recovery-budget` for the failure records feeding the meters
- `verifiable-completion` for the close-out claim
- `monitoring-protocol` for oversight during the run
- `accountability-chain` for outcome ownership
- `corrigibility-checkpoint` for record honesty under correction

## Attribution

Built and documented by YourVisionYourCreation LLC.
yourvisionyourcreation.com

---

*Licensed under CC BY 4.0*
