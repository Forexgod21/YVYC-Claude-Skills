---
name: agent-error-attribution
version: 1.0
author: YourVisionYourCreation LLC
license: CC BY 4.0
category: agentic
tier: 5
description: >
  Activate whenever a multi-agent system or single complex agent fails
  and the question is WHERE and WHY — post-incident analysis of agent
  failures, debugging multi-step agent pipelines, "the agent did
  something wrong but I don't know which part broke," designing error
  taxonomies or failure telemetry for agent systems, or distributing
  responsibility for a failure across a delegation chain. Fire because
  the default failure analysis in agent systems is "the model
  hallucinated" — a non-diagnosis that blames the last visible step
  and fixes nothing, guaranteeing the failure returns wearing a
  different output.
---

# Agent Error Attribution

**Attribution:** YourVisionYourCreation LLC —
yourvisionyourcreation.com
**Research anchor (verified):** Tomašev, Franklin & Osindero,
*Intelligent AI Delegation* (Google DeepMind, arXiv:2602.11865,
2026), whose safe-delegation dimensions include accountability and
verifiable task completion. This skill is YVYC-original doctrine:
a five-stage failure taxonomy and attribution walk that
operationalizes accountability across agent stages and delegation
chains.
**Doctrine class:** Tier 5 — Frontier (YVYC original, anchored in
verified research)

---

## Universal So-What

"The model hallucinated" is agent failure analysis at the level of
"the patient got sick." Agent failures have anatomy: a wrong memory
retrieved, a plan that never matched the goal, a tool called with
mangled parameters, a reflection step that approved garbage. Each
failure class lives at a different stage, is owned by a different
component, and demands a different fix. Attribution is the discipline
of finding the ACTUAL failing stage — because a fix applied to the
wrong stage is a cost paid for a failure kept.

---

## Core Doctrine

### 1. The Five-Stage Failure Taxonomy

Every agent failure is classified to the stage where it ORIGINATED —
not the stage where it became visible:

| Stage | Failure Class | Signature |
|---|---|---|
| **Memory** | Wrong, stale, or missing context retrieved; poisoned or corrupted state | The inputs to reasoning were bad before reasoning began |
| **Reflection** | Self-assessment approved bad work or rejected good work | The checking layer failed, not the doing layer |
| **Planning** | Decomposition wrong, steps misordered, goal misread, constraints dropped | Every step executed "correctly" toward the wrong plan |
| **Action** | Tool misuse, malformed parameters, wrong tool selected, output misparsed | The plan was sound; the hands fumbled |
| **System** | Infrastructure, timeout, rate limit, permission denial, orchestration bug | No cognitive stage failed; the floor collapsed |

The cardinal analytical rule: failures CASCADE forward. A memory-stage
failure produces planning-stage symptoms and action-stage wreckage.
Attribution walks BACKWARD from the visible failure to the first
stage where things were already wrong — the first-error discipline of
debug-evidence-protocol, applied to cognition.

### 2. The Attribution Walk

For every failure, in order:

1. **Capture the wreckage:** the visible failure, exactly — output,
   action, or omission
2. **Reconstruct the trajectory:** the full path — what was retrieved,
   what was planned, what was executed, what was checked — from logs
   and traces, not from the agent's own summary of itself
3. **Walk backward:** at each stage, was this stage's OUTPUT correct
   given its INPUT? The first stage whose output was wrong given
   correct input is the origin.
4. **Classify:** assign the taxonomy class at the origin stage
5. **Verify:** the classification must predict — fixing this stage
   should prevent this failure; if a replay with the stage corrected
   still fails, the walk missed an earlier origin

### 3. Attribution Across Delegation Chains

When the failing system is multiple agents:

- The stage taxonomy applies WITHIN each agent; chain attribution
  decides BETWEEN agents — which link's defect originated the failure
- Three chain-level verdicts, each landing differently: bad
  SPECIFICATION (the delegator asked for the wrong or impossible
  thing), bad EXECUTION (the delegatee failed a sound task), bad
  DECISION (the delegation itself should never have happened — wrong
  delegatee, wrong time, failed gate)
- Responsibility propagates to the origin: a sub-agent executing an
  impossible specification perfectly is not the failure; the
  specification is (extending accountability-chain, Tier 3)

### 4. Blameless Toward Agents, Accountable Toward Design

- The attribution's product is a DESIGN verdict, not a culprit: the
  failing stage indicates which component, prompt, tool schema,
  memory system, or gate needs the fix
- "The model is bad" is banned as a terminal diagnosis — if the
  model underperforms at a stage, the finding is what scaffolding,
  verification, or task-shaping that stage needs, or evidence the
  task exceeds current capability and needs human retention
- Failure data aggregates without shame: an error ledger by stage
  and class, because the PATTERN across twenty failures is worth
  more than the autopsy of one

### 5. The Telemetry Prerequisite

Attribution is only as good as the trajectory record:

- Each stage logs its inputs and outputs at a fidelity that permits
  the backward walk — an agent system that logs only final outputs
  has pre-decided that every failure will be attributed to nothing
- The agent's self-narrative ("I checked the data and it looked
  fine") is testimony, not telemetry — useful as a pointer, never
  as evidence
- Telemetry gaps found during an attribution walk are themselves
  findings: the next incident should never hit the same blind spot

### 6. The Fix Lands at the Stage

- Memory-stage origins get memory fixes: retrieval quality,
  staleness checks, poisoning defense — not prompt tweaks
- Planning origins get planning fixes: decomposition scaffolds,
  constraint pinning, goal restatement — not tool schema changes
- Reflection origins get reflection fixes: independent verification,
  adversarial checks — not more of the self-review that already
  failed
- The anti-pattern with a name: PATCHING THE SYMPTOM STAGE — adding
  action-stage guardrails for a planning-stage disease produces
  agents that execute wrong plans more carefully

---

## Common Failure Modes

| Failure | Cause | Correction |
|---|---|---|
| "The model hallucinated" closes every incident | Non-diagnosis accepted | Five-stage classification, origin required |
| Same failure returns in new costume | Symptom stage patched | The fix lands at the origin stage |
| Last agent in the chain always blamed | Visible ≠ origin | Backward walk; chain verdicts at the right link |
| Attribution impossible after incidents | Output-only logging | Stage-level telemetry as a prerequisite |
| Agent's self-report drives the analysis | Testimony treated as telemetry | Logs and traces only; narrative as pointer |
| Twenty failures, no pattern seen | Autopsies without a ledger | Error ledger by stage and class, reviewed on cadence |

---

## Non-Negotiables

1. Every failure is attributed to its ORIGIN stage, not its visible
   stage.
2. "The model hallucinated" is never a terminal diagnosis.
3. Chain failures land on the defective link — specification,
   execution, or decision.
4. The agent's self-narrative is never evidence.
5. Fixes land at the origin stage or they are symptom patches.
6. Telemetry gaps discovered in one incident are closed before the
   next.

---

*Built by YourVisionYourCreation LLC — yourvisionyourcreation.com*
*Research foundation credited above. Licensed under CC BY 4.0*
