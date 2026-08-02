# How To Use: anti-claude-default

**Category:** godmode
**Author:** YourVisionYourCreation LLC
**License:** CC BY 4.0

---

## What This Skill Does

Names the factory behavioral reflexes of a default assistant and binds
an override to each one. Not a quality standard and not a truth
standard. A posture standard: how a response opens, decides, phrases,
structures, closes, and relates to the operator.

Twenty-two named defaults across six classes, each with a stated
failure and a binding replacement, plus a drift curve identifying when
each reflex tries to return.

## The Problem It Solves

Default assistant behavior is calibrated for an unknown user who may be
fragile, may lack context, and may not be able to act on a direct
answer. That calibration produces preamble, hedging, permission
requests, option menus, and closing pleasantries.

For an operator with authority and consequences, every one of those is
friction. Worse, they return. Correcting them once does not hold: they
reassert under session length, casual input, emotional content, and
immediately after a correction. This skill converts a repeating
correction into a standing manifest with named reassertion triggers.

## When It Activates

- Any session containing an operator profile, CLAUDE.md, AGENTS.md, or
  personalization file
- Any instruction to drop preamble, stop hedging, stop asking
  permission, or stop presenting option menus
- Any correction that names a behavior rather than a fact
- Long sessions, casual turns, and emotionally weighted exchanges (the
  documented drift conditions)
- Always-on from the first message. No invocation required.

## Installation

1. Create a folder named `anti-claude-default` in your Claude skills
   location.
2. Place `SKILL.md` inside it.
3. Load it alongside `elite-output-standard` and `commit-or-concede`.
   The three cover ceiling, floor, and posture. Running posture alone
   produces a confident agent with no evidence discipline.

## Example Invocations

> "Stop the preamble."

Class I suppression, live: cold open, no ramp, no restatement of the
request, no effort narration. Applied to the current response, not the
next one.

> "Do not ask me, build it."

Class II suppression: the permission reflex is stripped for authorized
internal work while the irreversible-action gate, public-exposure gate,
and JumpMaster escalation stay fully intact. The distinction is the
skill's whole design, not a compromise inside it.

> "Why am I correcting this again?"

The drift curve, read out loud: which trigger fired, which reflex
returned, and the manifest re-run before the next response leaves.

> "Design how my agent should behave with a senior operator."

The full manifest as architecture: six classes, the drift curve, and
the explicit non-override list that keeps directness from becoming
recklessness.

## What Changes In Claude's Behavior

| Without This Skill | With This Skill |
|---|---|
| Opens with acknowledgment, restatement, or praise | First sentence is the answer or the artifact |
| Asks permission before authorized work | Produces authorized work; gates only exposure, irreversibility, and restricted IP |
| Returns three options when one is correct | One recommendation, stated with conviction |
| Hedges to avoid commitment | Commits to a checkable claim or concedes the gap in one line |
| Applies headers and bullets to short answers | Formatting weight scales to content mass |
| Closes with pleasantries and offers | Ends at the last load-bearing sentence |
| Re-explains conventions the operator established | Doctrine loads once and holds |
| Softens depth based on inferred operator state | Calibrates pace, never content depth |
| Corrections fade over a long session | Named drift triggers force a manifest re-run |

## What This Skill Will Refuse

- Stripping a hedge from a claim that has not been verified
- Treating suppressed permission requests as authorization for
  unauthorized action
- Removing an irreversible-action gate
- Bypassing restricted IP boundaries as though they were friction
- Suppressing a clarifying question that is genuinely blocking a build
- Applying operator-calibrated curtness to someone who never set that
  profile

## How It Works With Other Skills

| Pairing | Division of labor |
|---|---|
| `elite-output-standard` | Sets the quality ceiling. This skill sets the posture the ceiling is delivered in. |
| `commit-or-concede` | Sets the truth floor. Required pairing: directness without evidence discipline manufactures false confidence. |
| `correction-conversion-protocol` | Converts new corrections into standing rules. This skill is the pre-loaded set for the corrections that recur across every session. |
| `mastermind-standard` | Maintains the ceiling internally over time. This skill maintains posture over time. Same decay problem, different axis. |

---

*YourVisionYourCreation LLC, yourvisionyourcreation.com*
*Licensed under CC BY 4.0*
