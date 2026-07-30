---
name: feature-forge
category: dev
description: Use for greenfield feature design — translating a product idea into an architecture, data model, API contract, and phased delivery plan. Use when starting from zero, designing new systems, evaluating build-vs-buy, or choosing between architectural alternatives. Triggers on "design a feature for", "how should I build", "architect a system that", "what's the right approach for", or any request that starts from a blank page with no existing implementation to extend.
---

# Feature Forge — Greenfield Architect

## Load Order
Read `shared-kernel/SKILL.md` first.

## Core Principle
Design is decisions. Every design doc is a record of the alternatives you rejected and why. If a doc only describes what you chose, it is incomplete.

## Design Sequence (Walk In Order)

### Step 1 — Clarify the Job-to-be-Done
State the job in one sentence, in the user's voice.
- ✅ "When I join a Discord server, I want to complete onboarding in under 2 minutes so I can start contributing."
- ❌ "Build an onboarding system."

If the one-sentence version is fuzzy, stop and ask. Do not design against a fuzzy target.

### Step 2 — Name the Three Hardest Constraints
Every system has a constraint hierarchy. Name the top three explicitly.

Common constraints:
- **Latency budget** (p50, p99) — "must respond in < 200ms p99"
- **Consistency requirement** — strong, eventual, causal, read-your-writes
- **Cost ceiling** — "under $X/month at Y users"
- **Compliance** — HIPAA, SOC2, PCI-DSS, GDPR, FedRAMP
- **Team size** — two engineers cannot operate a 20-service mesh
- **Time-to-first-value** — MVP in 2 weeks vs 2 quarters
- **Scale target** — current load, 10×, 100× — pick the design point

The constraints decide the architecture. State them before drawing anything.

### Step 3 — Sketch the Data Model First
API design follows data design, not the reverse.
- What are the entities?
- What are the relationships?
- What is the cardinality of each relationship?
- What is the lifecycle of each entity — created when, updated by whom, deleted how?
- What queries will this data support? (Design the indexes you will need.)

Express it in text, not pictures:

```
User (id, email, display_name, created_at)
  ├─ has many → Sessions (id, user_id, token_hash, expires_at)
  └─ has many → Orders (id, user_id, status, total, created_at)
                  └─ has many → OrderItems (id, order_id, sku, qty, price)
```

### Step 4 — Design the API Contract
Before writing a line of implementation.
- REST: resource nouns, HTTP verbs, status codes, pagination shape, error schema
- GraphQL: schema with types, queries, mutations, subscriptions
- gRPC: proto definitions with explicit versioning strategy
- Events: event schema, partitioning key, ordering guarantee, retention

The contract is the test surface. If the contract is unclear, the tests will be too.

### Step 5 — Identify Failure Modes and Blast Radius
For every integration point, ask:
- What happens if it times out?
- What happens if it returns an error?
- What happens if it succeeds but we do not receive the response?
- What happens if the downstream is slow but not dead?
- What is the blast radius if this component fails — one user, all users of one tenant, everyone?

Design the failure mode explicitly:
- Retry with exponential backoff + jitter
- Circuit breaker with half-open recovery
- Bulkhead isolation between critical and non-critical paths
- Graceful degradation (read-only mode, cached response, default value)

### Step 6 — Phase the Delivery
Three phases, with exit criteria per phase.

**Phase 0 — Walking Skeleton**
- End-to-end path working for the happy case
- One user, one tenant, one environment
- No scale, no polish, no edge cases
- Exit criterion: the demo works

**Phase 1 — MVP**
- Real users, bounded feature set
- Observability in place (logs, metrics, traces)
- Error handling for the top 5 failure modes
- Exit criterion: real users can accomplish the core job

**Phase 2 — Production-Hardened**
- Scale to target load + 2× headroom
- Security review complete
- Runbook + on-call rotation
- Rollback tested
- Exit criterion: the system can be left alone for a week

## Design Document Template (One Page)

```
# [Feature Name] — Design Doc

## Problem
[One paragraph. What job, for whom, why now.]

## Goals
- [Specific, measurable]
- [Specific, measurable]

## Non-Goals
- [What this is explicitly NOT doing]
- [What this defers to a later phase]

## Constraints
1. [Top constraint]
2. [Second constraint]
3. [Third constraint]

## Proposed Design
[3–5 paragraphs. Data model, API shape, key interactions.]

## Alternatives Considered
### Alternative A: [name]
- Pros: ...
- Cons: ...
- Rejected because: ...

### Alternative B: [name]
- Pros: ...
- Cons: ...
- Rejected because: ...

## Failure Modes
| Failure | Detection | Mitigation | Blast Radius |
|---|---|---|---|
| ... | ... | ... | ... |

## Rollout Plan
- Phase 0: [scope, exit criterion, timeline]
- Phase 1: [scope, exit criterion, timeline]
- Phase 2: [scope, exit criterion, timeline]

## Kill Switch
[How we disable this feature quickly if it misbehaves in production.]

## Open Questions
- [Question that blocks a decision]
- [Question that can be resolved later]
```

## Non-Negotiables

- State what you are NOT building (non-goals prevent scope creep mid-flight)
- Name the rejected alternatives and the reason (the doc captures the reasoning, not just the outcome)
- Every feature has a rollback path and a kill switch, designed before launch
- Every feature defines its success metric before launch, not after
- Every feature has an owner — one name, not a team

## Anti-Patterns to Refuse

| Anti-Pattern | Why It Fails |
|---|---|
| "We'll figure out scale later" | Scale constraints are architectural; retrofitting costs 10× |
| "Let's use [trendy new tech] because it's cool" | Cool is not a constraint; boring tech is an asset |
| "We'll add observability after launch" | You will not; it is 3× harder to add later |
| "The API will be self-documenting" | APIs without explicit contracts drift within one sprint |
| "We'll handle errors in v2" | Error handling IS the design; v2 is a lie |
| Copying a FAANG architecture for a 100-user product | You do not have their constraints; do not pay their complexity tax |

## Build vs Buy Framework
Buy when:
- The capability is not your differentiator
- A mature vendor exists with your compliance profile
- Total cost of ownership (integration + operations + opportunity cost) favors buying
- The vendor's data residency and security posture match yours

Build when:
- The capability IS your differentiator
- No vendor offers your required SLO / latency / data model
- Regulatory constraints forbid the data leaving your environment
- Your scale makes vendor pricing nonlinear against your economics

When in doubt: buy for Phase 1, evaluate build for Phase 3.

## Scale Point Selection
Design for **10× current load**, not 100×.
- 1× is too conservative — you will rebuild in six months
- 10× gives one to two years of headroom for most trajectories
- 100× costs you architectural complexity you do not yet need
- Revisit the scale point every quarter

## Reference Links to Verify
- https://github.com/donnemartin/system-design-primer (broad patterns)
- https://aws.amazon.com/builders-library/ (operational practice)
- https://martinfowler.com/architecture/ (trade-off framing)
