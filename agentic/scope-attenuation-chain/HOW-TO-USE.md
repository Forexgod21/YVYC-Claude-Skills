# How To Use: scope-attenuation-chain

**Category:** agentic — Tier 5 (Frontier)
**Author:** YourVisionYourCreation LLC
**License:** CC BY 4.0
**Research anchor (verified):** Tomašev, Franklin & Osindero,
*Intelligent AI Delegation* (arXiv:2602.11865, 2026) — YVYC-original
doctrine extending its permission-handling dimension and this
library's `permission-attenuation` from principle to chain protocol.

---

## What This Skill Does

Enforces the physics of safe authorization: scope only narrows as it
travels through agent chains. Every delegation is a recorded grant
with a named parent, provenance is proven structurally instead of
self-reported, chain depth is bounded by visibility, revocation
cascades to every descendant instantly, and grants expire by default —
so no agent ever holds authority nobody can explain.

## When It Activates

- Designing permission systems for multi-agent chains
- Delegation token, grant, or authorization design
- "Where did this agent get the right to do that?"
- Auditing agent-to-agent authorization
- Any system where permissions could silently widen in transit

## Installation

1. Create a folder named `scope-attenuation-chain` in your Claude
   skills location.
2. Place `SKILL.md` inside it.
3. Claude activates it automatically on chained-authorization work.
4. Extends `permission-attenuation` (Tier 2) and pairs with
   `runtime-delegation-safety` (the gate checks the grant; this
   doctrine governs what the grant can contain).

## Example Invocations

> "Design the permission model for my agent pipeline."

The monotonic narrowing law installed: each hop's grant a strict
subset of its delegator's, enumerated scopes with bounds and parent
grants, expiry as the default, and depth limits set by how much of
the chain you can actually observe.

> "An agent three hops down did something nobody authorized."

The provenance question: show the chain from the action back to root
authority. If the chain exists, the audit finds the hop that granted
too much. If it does not, that is orphan authority — revoked on
discovery — and the audit hunts how it came to exist.

> "How do I revoke access across all my sub-agents at once?"

Revocation cascades: killing any grant structurally kills every grant
descended from it — one act, whole subtree, no per-hop cleanup, no
zombie survivors.

> "Our third-party integration needs delegation rights."

The cross-organization rule: a trust boundary gets maximum
attenuation, minimum duration, and full logging — the outside agent
receives the narrowest grant that serves the task, expiring the
moment the task ends.

## What You Get

- Authorization that structurally cannot widen in transit
- Every permission traceable to a root authority through recorded
  narrowing steps
- Audits that walk chains instead of collecting testimony
- One-act revocation across entire delegation subtrees
- Chain depth matched honestly to observation capacity

## What This Skill Will Refuse

- Any hop re-broadening scope
- Orphan authority surviving discovery
- Self-reported permissions as verification
- Unbounded chain depth over unobserved hops
- Permanent grants as a convenience default

---

*Built by YourVisionYourCreation LLC — yourvisionyourcreation.com*
