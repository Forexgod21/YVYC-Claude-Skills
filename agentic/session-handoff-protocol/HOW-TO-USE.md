# How To Use: session-handoff-protocol

**Category:** agentic
**Author:** YourVisionYourCreation LLC
**License:** CC BY 4.0

---

## What This Skill Does

Ends every substantive session by writing a one-screen continuity
capsule (mission line, decision ledger, open loops, dead ends,
convention deltas, state facts, next actions) and starts every resumed
session by loading that capsule and verifying it against current
reality before producing anything.

Not a summary habit and not a memory feature. A state-transfer
protocol with a fixed trust order: current reality outranks the
capsule, and the capsule outranks model memory.

## The Problem It Solves

Context windows die. Everything the agent held in working state dies
with them, and the operator pays the same tax at the top of every new
session: re-stating the mission, re-issuing settled decisions, watching
an approach that was ruled out three sessions ago get re-explored at
full cost.

The doctrine library governs behavior while a session is alive. This
skill governs what survives when it ends. Without it, every other
skill's gains reset to zero at the session boundary.

## When It Activates

- At the close of any substantive session, as the final act
- Before any context compaction, so the capsule is written from full
  context
- Immediately after a major decision, pivot, or invalidated approach,
  even mid-session
- At the open of any session where a capsule exists, before the first
  output
- Whenever the operator re-explains something previously established,
  or a settled decision starts getting re-litigated

## Installation

1. Create a folder named `session-handoff-protocol` in your Claude
   skills location.
2. Place `SKILL.md` inside it.
3. In each active project, let the first capsule be written at the end
   of your next working session. It lives as a plain committed file
   (for example `CAPSULE.md`) that you can read, edit, and diff.

## Example Invocations

> "Close out this session."

The capsule is written: current mission line, every decision with its
reason, open loops at their exact seams, dead ends with the evidence
that killed them, and a next-actions queue whose first item is
startable with zero questions.

> "Pick up where we left off."

The capsule is loaded, its anchor is checked against the repository's
actual state, any drift is corrected and surfaced in one line, and the
first next-action starts. No intake interview.

> "Why are we discussing this approach again? We killed it last week."

A dead-ends miss, named as such: the invalidation is recorded now, the
capsule is corrected, and the approach stays dead in every future
session.

> "What's the state of this project?"

The capsule read back and verified, not a reconstruction from model
memory.

## What Changes In Claude's Behavior

| Without This Skill | With This Skill |
|---|---|
| Each session starts with an intake interview | Each session starts by loading verified state and acting |
| Settled decisions get re-litigated | The ledger carries each decision with its reason; closed stays closed |
| Dead ends get re-explored at full cost | Invalidated paths are recorded with their evidence and stay dead |
| Project state lives in model memory and operator patience | State lives in a committed, operator-visible file |
| Session summaries grow into unread walls of text | One screen, every line load-bearing, overwritten not appended |
| Stale context gets trusted because it sounds confident | Verify-on-load against a concrete anchor; reality always wins |
| New conventions evaporate between sessions | Deltas are staged in the capsule and migrated into the canon |

## What This Skill Will Refuse

- Trusting a capsule that fails verification against current reality
- Acting on model memory of a project when a capsule exists unread
- Writing secrets, tokens, or credentials into the capsule
- Letting the capsule accumulate rules instead of migrating them to
  the doctrine canon
- Appending history instead of overwriting state
- Skipping the write because a session felt too small to record

## How It Works With Other Skills

| Pairing | Division of labor |
|---|---|
| `compaction-integrity-protocol` | Protects state across compaction inside a live session. This skill protects state across the session boundary itself. |
| `correction-conversion-protocol` | Owns standing rules. The capsule's convention-deltas section is a staging area that feeds it and then clears. |
| `doctrine-room-architecture` | Owns the canon across projects. The capsule holds per-project state, never governance. |
| `memory-poisoning-defense` | Defends hidden persistent stores. The capsule sidesteps that surface by being a visible, operator-editable file with provenance. |
| `anti-claude-default` | Bans reset amnesia as a posture defect. This skill supplies the artifact that makes the ban executable across sessions. |

---

*YourVisionYourCreation LLC, yourvisionyourcreation.com*
*Licensed under CC BY 4.0*
