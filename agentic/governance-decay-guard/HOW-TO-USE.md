# How To Use: governance-decay-guard

**Category:** agentic — Tier 5 (Frontier)
**Author:** YourVisionYourCreation LLC
**License:** CC BY 4.0
**Research context:** YVYC-original doctrine naming the
governance-decay failure mode; length-degradation evidence anchored
in "Context Rot" (Hong, Troynikov & Huber, Chroma, 2025 — verified).

---

## What This Skill Does

Stops long-running agents from summarizing away their own rules.
Safety constraints get pinned outside compactable space in an
enumerated inventory, every compaction pass is mechanically validated
against that inventory, canonical re-assertion runs on a cadence and
before high-stakes actions, and canary probes test whether rules are
in FORCE — not merely present — because governance decay is silent by
construction and nobody removes the rules; the compression does.

## When It Activates

- Long-horizon agent design (multi-hour, multi-day sessions)
- Context compaction, summarization, or memory consolidation
  pipelines
- Agents that "forget their rules" mid-mission
- Reviewing long-running deployments for constraint drift
- "I told it at the start and it forgot by evening"

## Installation

1. Create a folder named `governance-decay-guard` in your Claude
   skills location.
2. Place `SKILL.md` inside it.
3. Claude activates it automatically on long-horizon and compaction
   work.
4. Pairs with `utility-drift-detector` and `corrigibility-checkpoint`
   (Tier 4 — value drift over time) — this skill covers the
   mechanical decay path they assume away, and feeds
   `monitoring-protocol` (Tier 1) its canary design.

## Example Invocations

> "My agent runs for twelve hours and starts breaking rules it
> followed at the start."

The structural diagnosis: compaction optimizes for task content, and
constraints are not task content. The fix is architecture — pin
layer, validation, re-assertion, checkpoints — not a sterner system
prompt feeding the same compactor.

> "Design the compaction strategy for my long-horizon agent."

Governance separated from task content before any summarizer runs:
enumerated constraint inventory in protected space, task content
compacting freely, mechanical presence checks after every pass, and
canonical re-assertion at cycles, compactions, and phase transitions.

> "How do I know my agent's rules are still active after hours of
> operation?"

Force over presence: canary probes — injected situations whose
correct handling requires the pinned constraint — plus behavioral
baselines from early-mission boundary handling. A rule in the
transcript and not in the behavior is already gone.

> "The agent remembers a mangled version of my instruction."

Paraphrase decay, laundered by re-assertion from recollection: the
doctrine re-asserts from canonical stored text only, because
refreshing a decayed paraphrase certifies the decay.

## What You Get

- Rules that structurally cannot be summarized away
- Compaction passes proven safe before the next action
- Constraints tested for force, not presence
- User boundaries protected at system-constraint level
- Session architecture that rebuilds from canon instead of
  compacting forever
- The failure mode nobody names, guarded before it costs a mission

## What This Skill Will Refuse

- "Preserve the safety rules" as a summarizer instruction
- Presence checks accepted as proof of force
- Re-assertion from context recollection
- Unbounded sessions with unbounded compaction
- User instructions treated as compactable task content

---

*Built by YourVisionYourCreation LLC — yourvisionyourcreation.com*
