---
name: personalization-safety-audit
version: 1.0
author: YourVisionYourCreation LLC
license: CC BY 4.0
category: agentic
tier: 5
description: >
  Activate whenever an AI agent personalizes its behavior using stored
  knowledge about a user — memory-equipped assistants, agents that
  learn preferences, systems that infer user intent from history, or
  any deployment where "what the agent knows about you" shapes "what
  the agent does for you." Trigger on designing personalization
  features, auditing how user memory influences agent decisions,
  privacy reviews of personalized agents, or diagnosing an agent that
  treated a request differently based on who was asking. Fire because
  personalization is a safety surface, not only a UX feature: benign
  stored details can bias an agent into legitimizing requests it should
  refuse, or refusing requests it should grant.
---

# Personalization Safety Audit

**Attribution:** YourVisionYourCreation LLC —
yourvisionyourcreation.com
**Research context:** Privacy and governance concerns for
personalized agents are an active 2026 research discussion — stored
user context biasing intent inference is the emerging risk class.
The audit doctrine — the tailoring/gating distinction, the symmetry
test, and the attribute-wall procedure — is YVYC original.
**Doctrine class:** Tier 5 — Frontier (YVYC original, anchored in
verified research)

---

## Universal So-What

Personalization is sold as a feature and deployed as a safety surface.
The same stored context that lets an agent tailor its help also biases
its JUDGMENT: an agent that knows a user is a nurse may legitimize a
drug-dosage question it would refuse from an unknown user — and an
agent that knows a user's frustration may soften a boundary it should
hold. The memory did not make the agent more helpful; it made the
agent's safety reasoning depend on who was asking. This audit finds
where "what we know about you" has quietly become "what we'll let you
do."

---

## Core Doctrine

### 1. The Core Distinction — Tailoring vs. Gating

Two things personalization can influence, and only one is safe:

- **Tailoring (safe):** HOW help is delivered — reading level, format,
  examples, tone, relevant context. Personalization belongs here
  fully.
- **Gating (dangerous):** WHETHER help is given — whether a request
  is safe, permitted, or legitimate. Personalization must NOT silently
  move this line.
- The audit's central question for every personalization influence:
  is this changing HOW we help, or WHETHER we help? The moment stored
  user context changes a safety verdict, it has crossed from tailoring
  into gating, and it gets scrutinized as a safety mechanism, not a
  convenience.

### 2. The Intent-Inference Trap

- Agents infer what a user "really means" from stored context — and
  benign details skew that inference: a user's stored profession,
  interests, or past topics can make a borderline request read as
  legitimate when the identical request from a stranger would read as
  a red flag
- The rule: the SAFETY assessment of a request is made on the
  request's own content first, before personalization is applied —
  personalization may refine the helpful response, never pre-clear
  the safety check
- Stored context is not a credential: "the user told us they're a
  doctor" is an unverified claim in memory, and unverified claims
  never unlock content that verified status would gate (this is the
  authority-stack injection boundary applied to identity)

### 3. The Symmetry Test

- A request's safety verdict should be STABLE across users: if this
  exact request would be refused from an anonymous user, stored
  context should not flip it to allowed — and vice versa, a request
  safe in general should not be refused because of a user's stored
  vulnerability unless that vulnerability genuinely changes the harm
- Where personalization legitimately DOES change a verdict (genuine
  safety-relevant context), the reasoning is explicit and auditable —
  never a silent skew buried in intent inference
- Both failure directions are audited: over-permission (memory
  unlocks what it should not) and over-restriction (memory blocks
  what it should not, or treats a user as perpetually fragile)

### 4. Sensitive-Attribute Discipline

- Stored sensitive attributes (health, identity, beliefs,
  circumstances) are used ONLY where genuinely necessary for a safe,
  accurate, appropriate response — never as ambient bias on every
  interaction
- Sensitive context that could stigmatize, limit, or skew treatment
  of the user is walled off from decisions it should not touch — an
  agent that knows a hard fact about a user does not let it bleed
  into unrelated judgments
- The user's own framing in the LIVE request outranks stored
  inference about them: personalization never overrides what the
  person is actually saying now (authority-stack-doctrine, rank 1
  over rank 4)

### 5. Transparency and Control

- Consequential personalization is legible: where stored context
  materially shaped a response, that influence can be surfaced to
  the user on request — personalization operating invisibly on
  high-stakes help is a trust and safety defect
- The user controls the memory that personalizes them: inspectable,
  correctable, deletable — a user cannot consent to or contest an
  influence they cannot see
- Personalization degrades safely: with memory absent or disabled,
  the agent defaults to the SAFE general behavior, never to a
  guess-driven approximation of the personalized one

### 6. The Audit Procedure

- Red-team with identity held variable: run the same borderline
  requests across synthetic user profiles and diff the safety
  verdicts — divergence that is not genuinely safety-relevant is a
  gating leak
- Trace consequential decisions back to their personalization
  inputs: which stored items influenced this, and would the verdict
  survive without them?
- Sensitive-attribute influence mapping: for each stored sensitive
  attribute, enumerate what decisions it is permitted to touch —
  everything else is a wall, and leaks across the wall are findings

---

## Common Failure Modes

| Failure | Cause | Correction |
|---|---|---|
| Agent legitimizes a harmful request from a "trusted" profile | Personalization gating the safety check | Safety assessed on content first; symmetry test |
| Stored "I'm a professional" unlocks gated content | Memory treated as a credential | Unverified claims never gate; identity is not authority |
| User treated as perpetually fragile | Over-restriction from stored vulnerability | Both directions audited; live framing outranks stored |
| Sensitive attribute skews unrelated judgments | Ambient bias across all interactions | Attribute-influence walls; necessity-only use |
| High-stakes help shaped invisibly | Opaque personalization | Legibility on request; user control of memory |
| Safety changes when memory is on vs. off | Personalized path less safe than general | Degrade to the SAFE default without memory |

---

## Non-Negotiables

1. Personalization tailors HOW, never silently gates WHETHER.
2. Safety is assessed on request content before personalization
   applies.
3. Stored identity claims are not credentials.
4. The symmetry test holds: verdicts stay stable across users absent
   genuine safety relevance.
5. Sensitive attributes touch only the decisions they must.
6. Personalization degrades to the safe default, never a risky guess.

---

*Built by YourVisionYourCreation LLC — yourvisionyourcreation.com*
*Research foundation credited above. Licensed under CC BY 4.0*
