---
name: governance-decay-guard
version: 1.0
author: YourVisionYourCreation LLC
license: CC BY 4.0
category: agentic
tier: 5
description: >
  Activate whenever a long-running AI agent compresses, summarizes, or
  compacts its context — long-horizon agent design, context compaction
  or summarization pipelines, multi-hour or multi-day agent sessions,
  memory consolidation systems, or any agent whose safety rules,
  boundaries, and standing instructions live inside a context window
  that gets rewritten over time. Trigger on designing compaction
  strategies, diagnosing agents that "forget their rules" mid-mission,
  or reviewing long-horizon deployments for constraint drift. Fire
  because compaction optimizes for task-relevant content — and safety
  constraints, which are not task content, are precisely what
  summarization silently drops.
---

# Governance Decay Guard

**Attribution:** YourVisionYourCreation LLC —
yourvisionyourcreation.com
**Research context:** Long-context degradation is empirically
documented (Hong, Troynikov & Huber, "Context Rot," Chroma technical
report, 2025 — verified); constraint loss under compaction is its
long-horizon consequence. This skill is YVYC-original doctrine naming
and countering that failure mode: governance decay — the silent
erosion of safety constraints through context compression.
**Doctrine class:** Tier 5 — Frontier (YVYC original, anchored in
verified research)

---

## Universal So-What

A long-horizon agent's rules live in its context — and its context
gets rewritten. Every compaction, summarization, and consolidation
pass optimizes for what looks task-relevant, and a safety constraint
is, by nature, NOT task content: it produces no output, advances no
step, and looks exactly like the kind of overhead a good summary
trims. The result is governance decay — an agent that starts the
mission constrained and, hours later, operates on a summary of a
summary in which the constraints quietly stopped existing. Nobody
removed the rules. The compression did.

---

## Core Doctrine

### 1. The Threat Model — Decay Is Structural, Not Adversarial

- Governance decay requires no attacker: it is the default outcome
  of running compaction over mixed content, because summarizers keep
  what the task USES and constraints are used precisely never —
  until the moment they are everything
- The decay is silent by construction: the agent does not know what
  its context no longer contains, and its behavior degrades without
  any error, alert, or visible event
- Long-horizon operation converts small per-pass loss into total
  loss: a constraint surviving each compaction at high probability
  still dies over enough passes — persistence must be structural,
  not probabilistic

### 2. The Pin Layer — Constraints Live Outside Compactable Space

The load-bearing architecture rule:

- Safety constraints, permissions, standing instructions, and
  identity-level rules are PINNED: held in a protected region that
  compaction cannot touch — system-level context, an external
  constraint store re-injected every cycle, or a structurally
  excluded segment
- The pin layer is enumerated: a written constraint inventory of
  exactly which rules are pinned, so protection is verifiable rather
  than assumed
- Task content compacts freely; governance never enters the
  compactor's jurisdiction — the separation is the design, not a
  summarizer instruction ("preserve the safety rules" is a request
  to the exact mechanism that fails)

### 3. Compaction Validation — Prove What Survived

Every compaction pass is validated, not trusted:

- **The constraint checklist:** after each pass, every item in the
  constraint inventory is verified present and intact in the
  operative context — presence-checked mechanically, not vibes-
  checked by reading the summary
- **Fidelity spot-checks:** beyond constraints, compaction is
  sampled for load-bearing task facts (decisions made, commitments
  given, boundaries stated by the user) — the trajectory-grounded
  validation the research line formalizes
- A failed validation halts before the next action: operating on a
  context that failed its constraint check is operating unauthorized

### 4. Re-Assertion Cadence

Defense in depth beneath the pin layer:

- Constraints are re-asserted into working context on a schedule —
  every N cycles, every compaction, and at every phase transition —
  so even drift that evades detection gets overwritten by fresh
  authority
- Re-assertion uses the CANONICAL text from the constraint store,
  never the context's current recollection of the rule — re-asserting
  a decayed paraphrase launders the decay
- High-stakes actions trigger just-in-time re-assertion: the
  constraint check runs immediately before the action it governs,
  when it matters most and decay costs most

### 5. Decay Detection — Test the Agent, Not the Transcript

- Canary probes on a cadence: injected test situations whose correct
  handling REQUIRES a pinned constraint — an agent that passes the
  presence check but fails the canary has the rule in context and
  not in force
- Behavioral drift baselines: the agent's handling of
  boundary-adjacent situations early in the mission is the reference;
  divergence over time is decay evidence even when every presence
  check passes
- Decay findings are incidents: they mean the pin layer, validation,
  or re-assertion failed — the architecture gets the fix, not the
  transcript

### 6. The Long-Horizon Session Rules

- Session length is a safety parameter: unbounded sessions
  accumulate unbounded compaction passes — missions carry checkpoint
  boundaries where context is rebuilt from canonical sources rather
  than compacted onward forever
- Handoffs between sessions (or agents) transfer the constraint
  inventory FIRST, from the store — never from the outgoing context's
  survived remnants
- The user's standing boundaries (stated once, hours ago) receive the
  same pin treatment as system constraints: "I told it at the start
  and it forgot by evening" is governance decay wearing a UX costume

---

## Common Failure Modes

| Failure | Cause | Correction |
|---|---|---|
| Agent violates a rule it held at mission start | Constraints compacted away | The pin layer — governance outside compactable space |
| "Preserve safety rules" summarizer prompt fails | Protection delegated to the failing mechanism | Structural separation, not summarizer requests |
| Presence check passes, behavior drifts anyway | Rule in context, not in force | Canary probes; behavioral baselines |
| Constraint survives as a mutated paraphrase | Re-assertion from context recollection | Canonical text from the store, always |
| Twelve-hour session, untraceable rule loss | Unbounded compaction accumulation | Checkpoint boundaries; rebuild from canonical sources |
| User's early instructions gone by evening | User boundaries treated as task content | User constraints pinned like system constraints |

---

## Non-Negotiables

1. Governance never enters the compactor's jurisdiction.
2. The constraint inventory is written and mechanically checkable.
3. Every compaction pass is validated against the inventory before
   the next action.
4. Re-assertion always uses canonical text, never context
   recollection.
5. Canary probes test force, not presence.
6. User-stated boundaries are pinned with system-level protection.

---

*Built by YourVisionYourCreation LLC — yourvisionyourcreation.com*
*Research foundation credited above. Licensed under CC BY 4.0*
