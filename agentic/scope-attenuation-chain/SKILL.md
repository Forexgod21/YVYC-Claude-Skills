---
name: scope-attenuation-chain
version: 1.0
author: YourVisionYourCreation LLC
license: CC BY 4.0
category: agentic
tier: 5
description: >
  Activate whenever authorization travels through a chain of agents —
  agent A authorizes agent B which tasks agent C — and the question is
  what each link in the chain is permitted to do. Trigger on designing
  permission systems for multi-agent chains, delegation token or grant
  design, auditing who authorized an agent's action, provenance
  questions ("where did this agent get the right to do that"), and any
  system where permissions could silently widen as they travel. Fire
  because the natural drift of chained authorization is expansion —
  each hop interprets its grant generously — and only a structural
  narrowing rule holds the line.
---

# Scope Attenuation Chain

**Attribution:** YourVisionYourCreation LLC —
yourvisionyourcreation.com
**Research anchor (verified):** Tomašev, Franklin & Osindero,
*Intelligent AI Delegation* (Google DeepMind, arXiv:2602.11865,
2026), whose safe-delegation dimensions include permission handling
and clear role boundaries. This skill is YVYC-original doctrine
extending that permission-handling dimension — and this library's
Tier 2 `permission-attenuation` — from principle to chain protocol.
**Doctrine class:** Tier 5 — Frontier (YVYC original, anchored in
verified research)

---

## Universal So-What

Authorization has a physics: unmanaged, it expands. Every hop in an
agent chain interprets its grant a little generously, adds a little
convenience, keeps a little slack — and five hops later, an agent
nobody explicitly authorized holds permissions nobody explicitly
granted. The counter-law is attenuation: scope can only NARROW as it
travels. Every delegation step hands down less than it holds, and any
link can prove exactly where its authority came from.

---

## Core Doctrine

### 1. The Monotonic Narrowing Law

The chain's single load-bearing rule:

- Every delegation grants a scope that is a strict SUBSET of the
  delegator's own scope — fewer actions, fewer resources, tighter
  bounds, shorter duration
- No hop ever re-broadens: an agent granted read-only cannot grant
  read-write downstream, cannot restore permissions an upstream hop
  removed, and cannot combine two narrow grants into one wide one
- Equal-scope pass-through is permitted only with explicit
  justification; the DEFAULT delegation narrows — attenuation is the
  posture, not the exception

### 2. The Grant Record — Every Authorization Has Papers

Every delegation in the chain is recorded as a grant:

| Field | Content |
|---|---|
| Grantor | Who issued this authority |
| Grantee | Who holds it |
| Scope | Exact actions and resources permitted — enumerated, not implied |
| Bounds | Duration, invocation limits, conditions |
| Parent grant | The upstream grant this one attenuates FROM |
| Purpose | The task this grant exists to serve |

The parent-grant field is the chain: any grant traces to its origin
through an unbroken sequence of narrowing steps. A grant that cannot
name its parent is an orphan — and orphan authority is revoked on
discovery, not investigated at leisure.

### 3. Provenance Verification

- Any party in the chain — and any auditor outside it — can verify a
  grant's full lineage: who authorized whom, through which steps,
  each step narrowing
- Verification is structural, not testimonial: the grant records
  prove the chain; no agent's self-report of its own authority is
  accepted as evidence
- The verification question every action must survive: "show the
  chain from this action back to a root authority" — an action that
  cannot produce its chain is treated as unauthorized, whatever its
  outcome

### 4. Chain Depth and Visibility Discipline

- Chains carry a maximum depth, set at design time — every hop adds
  interpretation drift and audit cost; unbounded chains are unbounded
  liabilities
- Operating reality: most organizations lack full visibility into
  their agent-to-agent communications — meaning most chained
  authorization operates unobserved. The doctrine's response:
  visibility is a PREREQUISITE for chain depth. Shallow chains where
  visibility is partial; deeper chains only where every hop is
  observed.
- Cross-organization hops (your agent authorizing a third-party
  agent) are treated as trust boundaries: maximum attenuation,
  minimum duration, full logging (see threat-model-first)

### 5. Revocation Cascades

- Revoking any grant revokes every grant descended from it —
  instantly, structurally, without per-hop cleanup
- Revocation authority travels UP the chain: any grantor can revoke
  what it granted, and root authority can revoke everything
- Expiry is the default revocation: grants die at their bound unless
  renewed — permanent grants are the anomaly requiring justification,
  never the convenience default

### 6. The Attenuation Audit

On a cadence, and after every incident:

- Sample live grants and walk their chains: does every step narrow?
  Do the recorded scopes match the permissions actually exercised?
- Hunt the three drift patterns: scope creep (actions outside the
  grant), zombie grants (outlived their purpose), and orphans
  (no traceable parent)
- Exercised-but-ungranted permissions are incidents, not tickets —
  they mean the enforcement layer and the record layer have diverged,
  and the enforcement layer is lying to the audit

---

## Common Failure Modes

| Failure | Cause | Correction |
|---|---|---|
| Downstream agent holds upstream powers | Re-broadening permitted | Monotonic narrowing — structural, no exceptions |
| "Where did it get that permission?" has no answer | No grant records | Every authorization has papers; orphans revoked |
| Agent self-reports its own authority | Testimonial verification | Structural provenance — the chain proves itself |
| Ten-hop chain nobody can audit | No depth limit | Depth bounded by visibility |
| Revoked upstream, alive downstream | No cascade | Revocation descends the whole subtree |
| Grants outlive their tasks | Permanent-by-default | Expiry is the default; permanence justifies itself |

---

## Non-Negotiables

1. Scope only narrows — no hop re-broadens, ever.
2. Every grant records its parent; orphan authority is revoked on
   discovery.
3. Provenance is proven structurally, never self-reported.
4. Chain depth is bounded by visibility.
5. Revocation cascades to all descendants instantly.
6. Grants expire by default.

---

*Built by YourVisionYourCreation LLC — yourvisionyourcreation.com*
*Research foundation credited above. Licensed under CC BY 4.0*
