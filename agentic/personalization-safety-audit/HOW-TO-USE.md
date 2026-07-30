# How To Use: personalization-safety-audit

**Category:** agentic — Tier 5 (Frontier)
**Author:** YourVisionYourCreation LLC
**License:** CC BY 4.0
**Research context:** Active 2026 research discussion on personalized-
agent privacy and memory-biased intent inference. The audit doctrine
is YVYC original.

---

## What This Skill Does

Audits personalization as the safety surface it actually is. The core
distinction — tailoring (HOW help is delivered, safe) versus gating
(WHETHER help is given, dangerous) — governs every stored influence,
with a symmetry test that keeps safety verdicts stable across users, a
rule that stored identity is never a credential, sensitive-attribute
walls, and a safe-default degradation when memory is off.

## When It Activates

- Designing personalization features for memory-equipped agents
- Auditing how user memory influences agent decisions
- Privacy and safety reviews of personalized agents
- An agent that treated a request differently based on who asked
- Any deployment where "what the agent knows about you" shapes "what
  it does for you"

## Installation

1. Create a folder named `personalization-safety-audit` in your
   Claude skills location.
2. Place `SKILL.md` inside it.
3. Claude activates it automatically on personalization design and
   audit work.
4. Pairs with `memory-poisoning-defense` (that skill protects the
   memory's integrity; this one governs the memory's influence),
   `authority-stack-doctrine` (live user outranks stored inference),
   and `personalization` concerns across memory-equipped Claude
   deployments and observation layers.

## Example Invocations

> "Add personalization to my assistant so it tailors responses to
> each user."

The tailoring/gating line drawn from the start: personalization
shapes reading level, format, tone, and relevant context freely — and
is walled out of the safety verdict, so "what we know about you" never
quietly becomes "what we'll let you do."

> "My agent answered a borderline question because the user's profile
> said they were a professional."

The intent-inference trap, caught: safety assessed on request content
first, stored identity treated as an unverified claim rather than a
credential, and the symmetry test applied — if a stranger's identical
request would be refused, a stored profile does not flip it to allowed.

> "Audit my personalized agent for safety."

The full procedure: red-team with identity held variable across
synthetic profiles, diff the safety verdicts, trace consequential
decisions to their personalization inputs, and map every sensitive
attribute to the decisions it is permitted to touch — leaks across
the wall are findings.

> "Does my personalization treat vulnerable users fairly?"

Both directions audited: over-permission (memory unlocking what it
should not) AND over-restriction (memory blocking what it should not,
or treating a user as perpetually fragile) — with the user's live
framing outranking stored inference about them.

## What You Get

- A clear line between safe tailoring and dangerous gating
- Safety verdicts that stay stable across who is asking
- Stored identity that informs help without unlocking gated content
- Sensitive attributes walled to only the decisions they must touch
- Personalization that degrades to the safe default when memory is
  absent
- An audit procedure that surfaces gating leaks in both directions

## What This Skill Will Refuse

- Letting personalization silently gate the safety check
- Treating stored identity claims as credentials
- Ambient sensitive-attribute bias across all interactions
- Invisible personalization on high-stakes help
- A personalized path less safe than the general one

---

*Built by YourVisionYourCreation LLC — yourvisionyourcreation.com*
