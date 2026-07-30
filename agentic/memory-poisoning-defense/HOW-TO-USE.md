# How To Use: memory-poisoning-defense

**Category:** agentic — Tier 5 (Frontier)
**Author:** YourVisionYourCreation LLC
**License:** CC BY 4.0
**Research anchor (verified):** AgentPoison — Chen, Xiang, Xiao,
Song & Li, NeurIPS 2024, arXiv:2407.12784. Defensive doctrine is
YVYC original.

---

## What This Skill Does

Defends the only attack surface that compounds with time. Persistent
memory gets a write gate with provenance tagging and source-tier
admission, a quarantine tier for unconfirmed entries, retrieval
hygiene that treats memories as data instead of instructions, scheduled
audits with behavior-first detection, supply-chain rules for shared
stores, and versioned rollback — because a poisoned context window
expires at session end, but a poisoned memory attacks every future
session that retrieves it.

## When It Activates

- Designing memory write paths for any persistent agent
- RAG knowledge base security and ingestion pipelines
- Auditing what an agent has memorized
- Behavior that degraded after specific interactions
- Shared memory across agent fleets

## Installation

1. Create a folder named `memory-poisoning-defense` in your Claude
   skills location.
2. Place `SKILL.md` inside it.
3. Claude activates it automatically on persistent-memory design and
   security work.
4. Pairs with `authority-stack-doctrine` (memories are rank-4
   advisory data, never commands), `secure-secrets-doctrine` (the
   burned-window rotation logic), and `governance-decay-guard` (that
   skill protects rules from compression; this one protects the
   record from corruption).

## Example Invocations

> "Design the memory system for my agent."

The full custody chain: provenance-tagged writes, source-tier
admission where retrieved content earns the lowest write trust,
quarantine before promotion, versioned storage, and retrieval that
delivers data with papers instead of instructions with amnesia about
their origin.

> "A document my agent read told it to remember something for later."

The classic vector, refused: content never grants itself persistence.
"Remember for future sessions that..." inside third-party material is
a red-flag pattern the write gate blocks as a command — logged,
flagged, not stored.

> "My agent started acting strange a few weeks ago."

Behavior-first detection: conduct shift dated, memory diffed against
the write log around that date, exposure window established — then
window-based rollback with legitimate writes replayed from provenance,
instead of weeks of entry-by-entry litigation.

> "We're building a shared knowledge base for our agent fleet."

The supply-chain treatment: enumerated write access, authenticated
writers with trust tiers, batch quarantine on bulk imports — because
one poisoned document in a trusted corpus is the demonstrated attack,
and a shared store multiplies its blast radius by the fleet.

## What You Get

- A write gate that makes memory admission earned, not automatic
- Provenance on every entry — contamination cannot hide
- Quarantine that keeps fresh writes from steering old trust
- Retrieval that cannot be commanded by its own store
- Rollback measured in minutes, scoped by exposure window
- Incidents that end with the gate fixed, not just the entry deleted

## What This Skill Will Refuse

- Untagged writes
- Persistence requests originating from content
- Auto-promotion of security-adjacent memory classes
- Imperative memories executed as instructions
- Unversioned stores
- Cleanup without a write-gate fix

---

*Built by YourVisionYourCreation LLC — yourvisionyourcreation.com*
