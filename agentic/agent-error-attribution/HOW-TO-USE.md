# How To Use: agent-error-attribution

**Category:** agentic — Tier 5 (Frontier)
**Author:** YourVisionYourCreation LLC
**License:** CC BY 4.0
**Research anchor (verified):** Tomašev, Franklin & Osindero,
*Intelligent AI Delegation* (arXiv:2602.11865, 2026) — YVYC-original
taxonomy and attribution doctrine operationalizing its
accountability dimension.

---

## What This Skill Does

Replaces "the model hallucinated" with anatomy. Every agent failure
gets classified to its ORIGIN stage — memory, reflection, planning,
action, or system — via a backward walk from the visible wreckage,
with chain-level verdicts (bad specification, bad execution, bad
delegation decision) that land responsibility on the defective link,
and fixes that land at the origin stage instead of decorating the
symptom.

## When It Activates

- Post-incident analysis of any agent failure
- Debugging multi-step agent pipelines
- "Something went wrong but I don't know which part broke"
- Designing failure telemetry and error taxonomies for agent systems
- Distributing responsibility across a delegation chain

## Installation

1. Create a folder named `agent-error-attribution` in your Claude
   skills location.
2. Place `SKILL.md` inside it.
3. Claude activates it automatically on agent failure analysis.
4. The forensics arm of `accountability-chain` (Tier 3) and
   `runtime-delegation-safety` (Tier 5); applies
   `debug-evidence-protocol`'s first-error discipline to cognition.

## Example Invocations

> "My agent gave a completely wrong answer — why?"

The attribution walk: wreckage captured, trajectory reconstructed
from logs (not the agent's story about itself), backward walk to the
first stage whose output was wrong given correct input, classification
verified by whether fixing that stage prevents the failure on replay.

> "My pipeline fails somewhere in the middle and I can't tell where."

The telemetry prerequisite, diagnosed first: if stages log only final
outputs, attribution was defeated before the incident happened. The
stage-level logging spec comes before the next debugging session.

> "Which agent in my chain is responsible for this mess?"

Chain verdicts: specification, execution, or decision — with
responsibility propagating to the origin. A sub-agent that perfectly
executed an impossible task is not your defect; the specification is.

> "We keep adding guardrails and the failures keep coming."

The named anti-pattern: patching the symptom stage. Action-stage
guardrails on a planning-stage disease produce agents that execute
wrong plans more carefully. The error ledger reveals which stage
actually generates the failures.

## What You Get

- Failure analysis with anatomy instead of shrugs
- Origins found by backward walk, verified by replay prediction
- Chain responsibility landing on the defective link
- An error ledger whose patterns outvalue any single autopsy
- Fixes that prevent recurrence because they land at the origin
- Telemetry that improves after every incident

## What This Skill Will Refuse

- "The model hallucinated" as a terminal diagnosis
- Blaming the last visible agent by default
- The agent's self-narrative as evidence
- Symptom-stage patches dressed as fixes
- Incident closure with the telemetry gap still open

---

*Built by YourVisionYourCreation LLC — yourvisionyourcreation.com*
