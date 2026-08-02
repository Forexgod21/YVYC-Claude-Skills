# How To Use: adversarial-verification-doctrine

**Category:** agentic
**Author:** YourVisionYourCreation LLC
**License:** CC BY 4.0

---

## What This Skill Does

Replaces single-pass self-review with adversarial verification. No
load-bearing claim ships on the generator's word alone: findings,
diagnoses, completion claims, and anything the operator will act on
must survive an independent attempt to kill them before they ship.

The internal red team, run before the operator, the codebase, or the
world runs the external one.

## The Problem It Solves

The reasoning that produced an error will re-approve that error,
because it still holds the premise that caused it. "I checked my work"
usually means the author re-read their own output with the same blind
spots loaded. That is proofreading an alibi, not verification.

The result is confident wrong answers shipping with the same tone as
confident right ones, and the operator paying the difference.

## When It Activates

Arms at session start; fires at claim-shipping moments:

- A finding, diagnosis, review result, or completion claim is about to
  be reported
- An irreversible or outward-facing action is about to be taken on the
  strength of a conclusion
- The operator asks "are you sure," "verify that," "check your work,"
  or "how confident are you"
- A discovery task (bug hunt, audit, research sweep) is about to be
  declared complete

It does not fire on trivia or working conversation. Proportional cost
is a core law, not an option.

## Installation

1. Create a folder named `adversarial-verification-doctrine` in your
   Claude skills location.
2. Place `SKILL.md` inside it.
3. Pair it with `commit-or-concede`. That skill sets the truth floor;
   this one supplies the machinery that earns a claim the right to be
   committed.

## Example Invocations

> "Are you sure that's the bug?"

The claim goes through a refutation pass: an independent look at the
evidence assigned to prove the diagnosis wrong. The verdict comes back
as confirmed with the surviving evidence, or refuted with the concrete
failure scenario that killed it.

> "Audit this codebase for security issues. Be thorough."

Diverse-lens sweep with loop-until-dry: passes continue until
consecutive passes return nothing new, and every finding is
adversarially verified before it reaches the report. A count target is
never treated as completion.

> "Ship it."

If the claim behind the ship is load-bearing and unverified, the gate
fires once: verified now, or shipped labeled plausible with that word
doing its honest work.

> "How confident are you?"

An answer in the taxonomy, not in adjectives: confirmed (attacked and
survived), plausible (reasoned, unattacked), or the gap conceded.

## What Changes In Claude's Behavior

| Without This Skill | With This Skill |
|---|---|
| "I checked my work" means the author re-read it | Verification is an independent pass assigned to kill the claim |
| Verifiers asked "does this look right?" | Verifiers instructed to refute, defaulting to refuted on uncertainty |
| Three identical reviewers, one shared blind spot | Distinct lenses: correctness, reproduction, security, completeness |
| Everything labeled "verified" | Confirmed reserved for claims that survived an attack; plausible stays honest |
| Panels on trivia, or no verification anywhere | Cost scales to stakes: nothing for trivia, panels for irreversible calls |
| Bug hunts end at a satisfying count | Discovery runs until consecutive passes come back dry |
| Claims killed by vibes | A refutation must state the concrete failure scenario |

## What This Skill Will Refuse

- Stamping "confirmed" on a claim that was never attacked
- Letting a verifier read the generator's reasoning before judging
- Convening a panel on trivia to perform rigor
- Accepting a refutation that names no concrete failure scenario
- Treating generator confidence as evidence
- Declaring a discovery task complete because the count feels
  sufficient

## How It Works With Other Skills

| Pairing | Division of labor |
|---|---|
| `commit-or-concede` | Sets the truth floor. This skill is the machinery that upgrades a claim from plausible to committed. |
| `verifiable-completion` | Owns evidence of completion. This skill owns whether the claim itself survives attack. |
| `stand-and-fix-doctrine` | Owns the response when the operator challenges shipped work. This skill runs the challenge before shipping. |
| `security-review-v2` | Owns security-domain findings discipline. This skill is the general verification layer any finding passes through. |
| `untrusted-input-firewall` | Guards what the agent takes in. This skill guards what it puts out. Together they close the loop. |

---

*YourVisionYourCreation LLC, yourvisionyourcreation.com*
*Licensed under CC BY 4.0*
