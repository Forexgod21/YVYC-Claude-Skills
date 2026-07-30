# How To Use: Verifiable Completion

**Category:** `agentic/` | **Tier 2, Intermediate** | **Skill 14**

## What This Skill Does

It makes the word "done" mean something. The agent cannot report a task
as complete unless it can produce evidence for every requirement and name
the check it ran to confirm it.

## Who This Is For

- Anyone delegating multi-step work to an agent and acting on the result
- Developers running Claude Code on real codebases
- Operators who have been told a task was finished and later found it was
  not
- Teams where a false completion claim has a downstream cost

## Installation

1. Copy the `verifiable-completion` folder into your Claude skills
   directory.
2. Confirm both files are present: `SKILL.md` and `HOW-TO-USE.md`.
3. The skill activates automatically whenever the agent is about to
   report work as done, finished, or ready.

## What Changes in Practice

**Before this skill:**
You ask for six changes. The agent reports "All done, everything is
updated." Four changes landed, one was skipped because a file was locked,
and one was applied to the wrong file. You find out in production.

**After this skill:**
The agent returns a PARTIAL report that leads with the gap: four
requirements MET with file paths and diff output as evidence, one NOT MET
with the lock error verbatim, one flagged for operator review because the
target file was ambiguous. One recommended next action attached.

## The Report You Will Receive

One of exactly three, never a blend:

| Report | Meaning |
|---|---|
| COMPLETE | Every requirement verified with evidence and a named check |
| PARTIAL | Something is missing, and the gap comes first in the report |
| BLOCKED | Work could not proceed, blocker quoted verbatim |

## Reading the Completion Ledger

Every report carries a ledger. Four columns, one row per requirement:

| Requirement | Evidence | Verified by | State |
|---|---|---|---|

Where to look first: the **Verified by** column. If a row says NOT
VERIFIED, that requirement is unproven no matter what the State column
claims. This is the column that catches optimistic reporting.

## The Verification Tiers

The agent records how strong its evidence is. You can read the tier and
know how much to trust the claim.

| Tier | What it means | Your read |
|---|---|---|
| 1 | A check that would fail if the work were wrong | Trust it |
| 2 | Direct observation of the changed state | Strong |
| 3 | A tool said it succeeded | Reasonable |
| 4 | Nothing threw an error | Weak, verify yourself |
| 5 | The agent remembers doing it | Not evidence |

Tier 4 alone cannot support a COMPLETE report under this skill. Nothing
failing is not the same as something working.

## Language This Skill Removes

You will stop seeing these:

- "Should be working now"
- "Should be all set"
- "Everything looks good"
- "Fixed" with no proof the original failure is gone

Every one of those hands verification back to you while sounding like it
took verification off your plate.

## Requesting a Stricter Standard

You can raise the floor at task start:

```
Run this migration. Tier 1 evidence only on every requirement.
No Tier 3 or below accepted in the ledger.
```

The agent will confirm the standard and hold to it, escalating rather
than downgrading when Tier 1 is out of reach.

## The Regression Rule on Fixes

When you ask for a fix, completion requires one extra thing: the agent
confirms the original failure no longer reproduces under the conditions
that caused it. A fix proven only by the absence of new errors does not
clear this skill.

## Pairs Well With

- `retry-recovery-budget` so failed steps cannot be silently dropped
  before close-out
- `agent-observability-doctrine` for the underlying record structure
- `human-in-loop-escalation` for when verification exceeds the agent's
  authority
- `accountability-chain` for ownership of the claim once made
- `monitoring-protocol` for checks during the run, not only at the end

## What This Skill Will Refuse

- Reporting COMPLETE with an unverified row in the ledger
- Merging separate requirements into one summarized claim
- Substituting a weaker evidence tier when the real check is unavailable
- Rounding a PARTIAL up because the remaining work looks minor
- Treating the absence of an error message as proof of success

## Attribution

Structured, translated, and built by YourVisionYourCreation LLC.
Research foundation: Tomasev, Franklin, and Osindero (2026),
*Intelligent AI Delegation*, Google DeepMind, arXiv:2602.11865.

---

*YourVisionYourCreation LLC, yourvisionyourcreation.com*
*Licensed under CC BY 4.0*
