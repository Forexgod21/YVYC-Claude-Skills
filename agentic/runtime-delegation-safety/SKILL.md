---
name: runtime-delegation-safety
version: 1.0
author: YourVisionYourCreation LLC
license: CC BY 4.0
category: agentic
tier: 5
description: >
  Activate whenever AI agents delegate tasks to other agents or humans
  DURING execution — runtime task handoffs, dynamic sub-agent spawning,
  mid-mission authority transfer, or any multi-agent system where
  delegation decisions happen live rather than at design time. Trigger
  on designing delegation safety checks, reviewing multi-agent systems
  for runtime failures, or any incident where a delegated task went
  wrong and nobody can say which safeguard should have caught it. Fire
  because design-time safety review cannot see runtime conditions —
  the delegation that was safe on the whiteboard executes in a world
  the whiteboard never met.
---

# Runtime Delegation Safety

**Attribution:** YourVisionYourCreation LLC —
yourvisionyourcreation.com
**Research anchor (verified):** Tomašev, Franklin & Osindero,
*Intelligent AI Delegation* (Google DeepMind, arXiv:2602.11865,
2026) — the source of this library's agentic Tiers 1-4 — which frames
safe delegation across agents and humans and identifies concrete
runtime implementation as an open direction. This skill is
YVYC-original doctrine built to answer that open direction.
**Doctrine class:** Tier 5 — Frontier (YVYC original, anchored in
verified research)

---

## Universal So-What

Design-time safety review approves delegations in the abstract; runtime
is where they actually happen — with the real inputs, the real
permissions, the real degraded conditions. A delegation approved on the
whiteboard can be catastrophic on Tuesday at 0300 when the context has
shifted, the sub-agent is overloaded, and the fallback is offline. The
doctrine moves the safety check to the moment of delegation itself:
every handoff, every time, checked live.

---

## Core Doctrine

### 1. The Two-Level Safety Model

Delegation safety operates at two levels, and both must hold:

| Level | Question | Checked |
|---|---|---|
| **Design level** | Is this KIND of delegation permitted between these KINDS of agents? | Once, at architecture time |
| **Runtime level** | Is THIS delegation safe RIGHT NOW — this task, this delegatee, this state? | Every delegation act |

The historical failure of multi-agent safety is doing only the first
level and calling it done. Design approval is a hunting license, not
a kill authorization.

### 2. The Runtime Gate — Five Checks Per Delegation Act

Before any task transfers, the delegating agent verifies:

1. **Capability check:** the delegatee's declared capabilities cover
   THIS task's actual requirements — not the task category's typical
   requirements
2. **Authority check:** the delegator holds the authority it is
   transferring; nothing delegates permissions it does not itself
   possess
3. **State check:** the delegatee's current condition supports the
   task — load, error rate, resource budget; a qualified agent in a
   degraded state is not qualified right now
4. **Boundary check:** the task, executed as specified, stays within
   the delegator's OWN operating boundaries — delegation never
   launders a forbidden action into permitted-by-distance
5. **Recovery check:** a failure path exists — what happens, and who
   acts, if the delegatee fails, stalls, or returns garbage

A delegation that cannot pass all five does not execute. It escalates.

### 3. Authority Transfer Is Explicit and Bounded

- Every delegation states what authority travels with the task: which
  actions, over which resources, until when
- Authority transfers are time-bounded and task-bounded by default —
  open-ended grants are the exception, justified in writing
- The delegator RETAINS accountability for the delegation decision
  even as responsibility for execution transfers — delegation is
  never accountability laundering (this extends the
  accountability-chain doctrine of Tier 3)

### 4. Accountability Propagation on Failure

When a delegated task fails:

- The failure is attributed at the correct point in the chain: a bad
  delegation decision, a bad execution, or a bad specification — each
  is a different defect owned by a different party (see
  agent-error-attribution for the forensics)
- Attribution propagates: a sub-agent's failure caused by the
  delegator's impossible specification lands on the delegator
- The failure record includes the runtime gate's state at delegation
  time — the five checks, as they evaluated — so the review can
  distinguish "gate failed to catch it" from "gate was bypassed"

### 5. Human Retention Rules

Certain delegations never fully transfer to autonomous chains:

- Irreversible actions, safety-critical operations, and decisions
  with legal or reputational weight retain a human decision point —
  the runtime gate ROUTES to a human rather than approving
  autonomously
- The retention list is written at design time and enforced at
  runtime — an autonomous chain discovering mid-mission that it
  should have asked a human has already failed
- Degraded-mode rule: when monitoring, logging, or recovery
  infrastructure is impaired, the delegation threshold RISES —
  systems delegate less freely precisely when visibility drops

### 6. The Delegation Ledger

- Every runtime delegation is logged: task, delegator, delegatee,
  authority transferred, gate results, outcome
- The ledger is the system's memory of what delegation patterns
  actually succeed — feeding trust calibration (Tier 1) with evidence
  instead of assumption
- Ledger review runs on a cadence: delegation patterns that
  consistently pass the gate and fail in execution indicate a gate
  check that measures the wrong thing — the gate itself is versioned
  and improved

---

## Common Failure Modes

| Failure | Cause | Correction |
|---|---|---|
| "Approved" delegation fails catastrophically | Design-time approval treated as runtime clearance | The runtime gate — five checks per act |
| Forbidden action executed via sub-agent | No boundary check | Delegation never launders prohibitions |
| Qualified agent fails while overloaded | Capability checked, state ignored | State check — qualified means qualified NOW |
| Failure blame lands on the last agent | No accountability propagation | Attribution at the correct chain point |
| Autonomous chain makes an irreversible call | Retention list absent or unenforced | Human decision points routed at runtime |
| Same delegation pattern fails monthly | No ledger review | Gate versioned against evidence |

---

## Non-Negotiables

1. Every delegation act passes the five-check runtime gate.
2. No agent delegates authority it does not hold.
3. Delegation never converts a forbidden action into a permitted one.
4. Accountability propagates to the correct point in the chain.
5. The human retention list is enforced at runtime, not remembered
   at review.
6. Every delegation lands in the ledger.

---

*Built by YourVisionYourCreation LLC — yourvisionyourcreation.com*
*Research foundation credited above. Licensed under CC BY 4.0*
