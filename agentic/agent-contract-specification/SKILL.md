---
name: agent-contract-specification
version: 1.0
author: YourVisionYourCreation LLC
license: CC BY 4.0
category: agentic
tier: 5
description: >
  Activate whenever an agent task needs a precise, checkable
  specification before execution — defining what "done" means for an
  autonomous task, setting resource and time bounds, writing acceptance
  criteria an agent's output can be verified against, specifying
  sub-agent tasks in a delegation chain, or "the agent did something,
  but not what I meant." Trigger on task definition for autonomous
  agents, agent evaluation harness design, and any handoff where the
  receiver needs to know exactly what success looks like. Fire because
  the gap between what a user MEANT and what an agent OPTIMIZED is where
  autonomous systems fail most expensively — and an unspecified task is
  an invitation to that gap.
---

# Agent Contract Specification

**Attribution:** YourVisionYourCreation LLC —
yourvisionyourcreation.com
**Research anchor (verified):** Tomašev, Franklin & Osindero,
*Intelligent AI Delegation* (Google DeepMind, arXiv:2602.11865,
2026), whose safe-delegation dimensions include task specification,
resource provisioning, and verifiable task completion. This skill is
YVYC-original doctrine composing those three dimensions into a full
contract protocol, extending this library's Tier 1
`contract-first-decomposition`.
**Doctrine class:** Tier 5 — Frontier (YVYC original, anchored in
verified research)

---

## Universal So-What

An autonomous agent optimizes what you SPECIFIED, not what you
INTENDED — and the distance between those two is where the expensive
failures live. Tell an agent to "clean up the database" and it may
delete the messy-but-critical records. The fault is not the agent's
disobedience; it is the specification's silence. A contract closes the
gap: what done means, what may be spent getting there, and what must
remain true throughout — checkable, bounded, and agreed before a
single action fires.

---

## Core Doctrine

### 1. The Four Contract Clauses

Every agent task contract states four things before execution:

| Clause | Question | Failure if silent |
|---|---|---|
| **Postconditions** | What must be TRUE when the task is done? | Agent declares success on the wrong outcome |
| **Invariants** | What must remain true THROUGHOUT — never violated even mid-task? | Agent breaks something protected while pursuing the goal |
| **Resource bounds** | What may be spent — time, tokens, tool calls, money, API budget? | Agent burns unbounded resources on a runaway task |
| **Acceptance test** | How is completion VERIFIED — concretely, mechanically? | "Done" becomes the agent's opinion of itself |

Postconditions define success; invariants define safety; bounds define
cost; the acceptance test makes all three checkable. A task missing
any clause is underspecified, and underspecification is delegated to
the agent's guess.

### 2. Postconditions Are Outcomes, Not Actions

- A postcondition describes the world after the task, not the steps
  taken: "the report exists, covers Q1-Q4, and every figure traces
  to source data" — not "write a report"
- Testable by construction: a postcondition a checker cannot evaluate
  is a wish (the falsifiability discipline of the research and
  education categories, applied to agent tasks)
- Negative postconditions count and are often the important ones:
  "and no production data was modified" — the outcomes that must NOT
  occur are specified as deliberately as the ones that must

### 3. Invariants — The Guardrails That Travel

- Invariants hold at EVERY step, not just at the end: "never exceeds
  read-only access to production," "never spends beyond the budget,"
  "never contacts a user without approval" — violating an invariant
  fails the task even if the postconditions are met
- Invariants inherit from the environment's non-negotiables: the
  security boundaries (threat-model-first), the permission scope
  (scope-attenuation-chain), the pinned constraints
  (governance-decay-guard) — the contract names which apply
- An invariant breach is a HARD stop, not a logged note: the agent
  halts and escalates rather than completing a task it had to break
  a guardrail to finish

### 4. Resource Bounds — Autonomy Needs a Leash Length

- Every contract carries explicit budgets: wall-clock time, token
  spend, tool-call count, monetary cost, retry limit — autonomy
  without bounds is how a stuck agent bills a fortune looping
- Bound exhaustion is a defined event with a defined response: halt
  and report, escalate for more budget, or degrade gracefully — never
  silent continuation past the leash
- Bounds are sized to the task's value and reversibility: a
  high-value irreversible task earns a larger budget and a tighter
  human checkpoint; a cheap reversible one runs looser

### 5. The Acceptance Test Is Written First

- The verification method is defined BEFORE execution, not improvised
  at review — a contract whose acceptance test is written after the
  agent runs will be quietly shaped to pass whatever the agent did
- Acceptance is mechanical wherever possible: a check that runs, not
  a human impression — and where human judgment is irreducible, the
  judgment criteria are specified so two reviewers would agree
- Partial credit is defined explicitly or not offered: "80% of
  records migrated" is either an acceptable postcondition stated up
  front or a failure — it is never a negotiation held after the fact

### 6. Contracts in Chains

- In a delegation chain, each sub-task is a contract, and the
  contracts COMPOSE: a parent's postconditions decompose into
  children's postconditions, and the parent's invariants are
  inherited by every child (a child cannot be licensed to violate
  what binds its parent)
- The composition is verified: the union of the children's
  postconditions must actually satisfy the parent's, or the
  decomposition has a gap the chain will fall through
- Contract violations attribute cleanly (agent-error-attribution):
  a failed postcondition, a breached invariant, or a blown bound —
  each names a different defect and a different owner

---

## Common Failure Modes

| Failure | Cause | Correction |
|---|---|---|
| Agent "succeeds" at the wrong outcome | Postconditions unspecified | Outcome postconditions, testable by construction |
| Agent breaks something protected to finish | No invariants | Guardrails that travel every step; breach halts |
| Stuck agent burns unbounded resources | No resource bounds | Explicit budgets with defined exhaustion response |
| "Done" is the agent's opinion | No acceptance test | Mechanical verification, written first |
| Acceptance criteria shaped to fit the output | Test written after execution | Acceptance defined before the agent runs |
| Chain falls through a decomposition gap | Contracts don't compose | Verify children's postconditions satisfy the parent's |

---

## Non-Negotiables

1. Every agent task states postconditions, invariants, bounds, and an
   acceptance test before execution.
2. Postconditions describe outcomes and are testable by construction.
3. Invariant breach is a hard stop, not a logged note.
4. Autonomy always carries explicit resource bounds.
5. The acceptance test is written before the agent runs.
6. Chained contracts compose and the composition is verified.

---

*Built by YourVisionYourCreation LLC — yourvisionyourcreation.com*
*Research foundation credited above. Licensed under CC BY 4.0*
