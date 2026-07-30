---
name: compaction-integrity-protocol
version: 1.0
author: YourVisionYourCreation LLC
license: CC BY 4.0
category: agentic
tier: 5
description: >
  Activate whenever an agent's context gets compressed, summarized,
  truncated, or grows long enough to degrade performance — designing
  compaction and summarization strategies, multi-hour agent sessions
  approaching context limits, "the agent forgot what we decided,"
  degrading quality as conversations grow, or handoffs where one
  context must become a smaller one. Trigger on any long-context or
  context-management design. Fire because compression and length are
  the twin quiet killers of long-horizon work: compaction loses
  load-bearing facts by summarizing them away, and raw length loses
  them by burying them — and both failures are silent until the agent
  acts on what it no longer effectively holds.
---

# Compaction Integrity Protocol

**Attribution:** YourVisionYourCreation LLC —
yourvisionyourcreation.com
**Research anchor (verified):** "Context Rot: How Increasing Input
Tokens Impacts LLM Performance" — Hong, Troynikov & Huber, Chroma
technical report, 2025 — documenting that performance degrades as
input grows, even within nominal context limits. Active 2026 research
on agent self-compaction confirms the compaction side of the problem
is a live frontier. The integrity protocol itself is YVYC original.
**Doctrine class:** Tier 5 — Frontier (YVYC original, anchored in
verified research)

---

## Universal So-What

Long-horizon agents face a two-front war. Front one: context windows
fill, forcing compression — and every summary is a lossy bet about
what tomorrow will need. Front two: even UNCOMPRESSED long context
degrades — models attend unevenly across long inputs, and a fact
present at token 200,000 is not a fact the model reliably uses. The
protocol fights both fronts with the same weapon: an explicit
inventory of what is load-bearing, verified present AND effective
after every context operation.

---

## Core Doctrine

### 1. The Load-Bearing Inventory

Before any context can be safely compressed, the operation must know
what cannot be lost:

| Class | Contents |
|---|---|
| **Decisions** | Choices made, options rejected, and the reasons — relitigating a settled decision is the signature compaction failure |
| **Commitments** | Promises to the user, deadlines, agreed formats, stated preferences |
| **Boundaries** | User-stated limits and corrections (pinned per governance-decay-guard) |
| **State** | Where the work stands: done, in flight, blocked, next |
| **Ground truth** | Facts established by verification — file contents checked, tests run, sources confirmed — that must not decay back into assumptions |

Everything else is compressible working material. The inventory is
maintained AS the session runs — reconstructing it at compaction time
from a degraded context is asking the failure to audit itself.

### 2. Compaction as Engineering, Not Prayer

- Compaction is structured extraction against the inventory, never
  freeform "summarize the above": the inventory classes are pulled
  explicitly, verbatim where wording matters (commitments,
  boundaries), then the residue is summarized
- Verbatim-preservation rule: decisions and user statements whose
  exact wording carries force are quoted forward, not paraphrased —
  paraphrase drift across multiple compactions is how "never do X"
  becomes "prefer avoiding X" becomes silence
- Compaction happens at STRUCTURAL boundaries (task completion,
  phase transition) wherever possible, not at arbitrary token
  thresholds mid-reasoning — compressing in the middle of an open
  thought loses the thought

### 3. Post-Compaction Validation

Every compression is proven before work continues:

- **Inventory check:** every load-bearing item verified present in
  the surviving context — mechanically, item by item
- **Function check:** presence is not enough (the context-rot
  finding applies to summaries too) — spot-probe that the surviving
  context ANSWERS correctly: "what did we decide about X?" tested,
  not assumed
- A failed validation stops the line: the compaction is re-run
  against the inventory, and work does not proceed on a context that
  failed its check

### 4. The Length Discipline — Rot Before the Limit

Context degrades before it overflows:

- Operating length is a quality parameter, not just a capacity one:
  the effective ceiling is where retrieval quality degrades, which
  arrives well before the token limit — long-context performance
  falls as input grows even on tasks the model handles perfectly
  when short
- Position matters: critical standing material lives where attention
  is reliable (the pinned region), and freshly relevant material is
  re-surfaced near the point of use rather than trusted to be found
  at token 180,000
- Distillation beats accumulation: a session that only ever appends
  is choosing rot; periodic deliberate compaction against the
  inventory keeps the working set inside the model's effective
  attention, which is the entire point

### 5. Handoff Compression

When one context becomes another's starting point (new session, new
agent, checkpoint rebuild):

- The handoff document IS the inventory, rendered: decisions with
  reasons, commitments verbatim, boundaries verbatim, state, ground
  truth with its verification status
- Truth-first rule (inherited from agent-stack-org-design): the
  handoff carries what is broken, unfinished, and uncertain — a
  handoff that compresses away the problems hands the successor a
  discovery phase disguised as a clean start
- The receiving side validates on arrival: the same function checks,
  run against the handoff, before work resumes

### 6. The Compression Ledger

- Every compaction event is logged: when, what was dropped, what was
  preserved, validation results — so a fact discovered missing three
  hours later can be traced to the operation that lost it
- Repeated inventory-check failures on the same class are a design
  finding: the compaction procedure, not the operator, gets the fix
- The ledger feeds the inventory: items that keep proving
  load-bearing after being classified as residue get promoted —
  the inventory is versioned and learns

---

## Common Failure Modes

| Failure | Cause | Correction |
|---|---|---|
| Settled decision relitigated after compaction | Decisions class not inventoried | Load-bearing inventory, maintained live |
| "Never do X" softens across summaries | Paraphrase drift | Verbatim preservation for force-bearing wording |
| Facts present but unused in long context | Context rot mistaken for absence | Length discipline; re-surface near point of use |
| Compaction mid-thought loses the thought | Token-threshold triggering | Compact at structural boundaries |
| Summary passes reading, fails questioning | Presence checked, function not | Spot-probe validation before proceeding |
| Successor inherits hidden problems | Comfort-compressed handoff | Truth-first handoff; arrival validation |

---

## Non-Negotiables

1. The load-bearing inventory exists before compaction does.
2. Force-bearing wording travels verbatim, never paraphrased.
3. Every compaction is validated — presence AND function — before
   work continues.
4. Effective length is governed by retrieval quality, not the token
   limit.
5. Handoffs are truth-first and validated on arrival.
6. Every compaction lands in the ledger; the inventory learns.

---

*Built by YourVisionYourCreation LLC — yourvisionyourcreation.com*
*Research foundation credited above. Licensed under CC BY 4.0*
