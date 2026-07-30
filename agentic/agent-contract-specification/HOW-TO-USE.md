# How To Use: agent-contract-specification

**Category:** agentic — Tier 5 (Frontier)
**Author:** YourVisionYourCreation LLC
**License:** CC BY 4.0
**Research anchor (verified):** Tomašev, Franklin & Osindero,
*Intelligent AI Delegation* (arXiv:2602.11865, 2026) — YVYC-original
contract protocol composing its task-specification,
resource-provisioning, and verifiable-completion dimensions;
extends Tier 1 `contract-first-decomposition`.

---

## What This Skill Does

Closes the gap between what a user meant and what an agent optimized.
Every autonomous task gets a four-clause contract before execution —
postconditions (what must be true), invariants (what must stay true
throughout), resource bounds (what may be spent), and an acceptance
test (how completion is verified) — with contracts that compose across
delegation chains and violations that attribute cleanly.

## When It Activates

- Defining "done" for any autonomous agent task
- Setting resource and time bounds for agent work
- Writing acceptance criteria agent output is verified against
- Specifying sub-agent tasks in a delegation chain
- "The agent did something, but not what I meant"
- Agent evaluation harness design

## Installation

1. Create a folder named `agent-contract-specification` in your
   Claude skills location.
2. Place `SKILL.md` inside it.
3. Claude activates it automatically on agent task definition.
4. Extends `contract-first-decomposition` (Tier 1) and pairs with
   `runtime-delegation-safety`, `scope-attenuation-chain`, and
   `agent-error-attribution` (Tier 5) — the contract supplies the
   invariants the gate checks and the criteria attribution measures
   against.

## Example Invocations

> "Set up an agent to clean up my database."

The contract before the action: postconditions ("duplicate rows
removed, no record referenced elsewhere deleted"), invariants
("read-only on production until the change is approved"), bounds
("under N operations, halt and report if exceeded"), and a mechanical
acceptance test — so "clean up" cannot quietly mean "delete the
messy-but-critical records."

> "How do I define 'done' for an autonomous task?"

Outcome postconditions, testable by construction, including the
negative ones ("and nothing in production was modified") — because
the outcomes that must NOT occur are where autonomous failures get
expensive, and they get specified as deliberately as the goal.

> "My agent got stuck and ran up a huge bill."

Resource bounds, the missing leash: explicit budgets for time,
tokens, tool calls, and money, with bound exhaustion as a defined
event — halt and report, escalate, or degrade — never silent
continuation past the leash.

> "I'm breaking a big task into sub-agent tasks."

Composing contracts: the parent's postconditions decompose into the
children's, the parent's invariants bind every child, and the
composition is verified — the union of children's postconditions must
actually satisfy the parent's, or the chain has a gap to fall through.

## What You Get

- Tasks specified before they run, not adjudicated after
- Success, safety, and cost each defined and each checkable
- Invariants that halt an agent rather than let it break a guardrail
  to finish
- Autonomy with a leash length matched to value and reversibility
- Acceptance tests written first, immune to being shaped to fit output
- Chain contracts that compose without decomposition gaps

## What This Skill Will Refuse

- Autonomous tasks with unspecified postconditions
- Missing invariants on anything touching protected resources
- Unbounded resource grants
- Acceptance criteria written after execution
- Decompositions whose parts don't provably sum to the whole

---

*Built by YourVisionYourCreation LLC — yourvisionyourcreation.com*
