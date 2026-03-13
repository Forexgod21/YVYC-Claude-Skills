# HOW TO USE — span-of-control

**Category:** Agentic
**Skill Version:** 1.0
**Author:** YVYC (Your Vision Your Creation)

---

## What This Skill Does

This skill makes Claude's reliable operating limit visible before you rely on it.

When a task is too complex or involves too many parallel threads for Claude to
execute reliably, this skill catches it before execution begins — not after
quality has already degraded silently. You get options. You decide how to proceed.

---

## The Problem It Solves

Claude can attempt more than it can reliably execute. When span is exceeded,
quality degrades — but the output still looks complete. You don't find out
until you use it and something is wrong.

**span-of-control** stops that. Claude assesses its reliable limit before
accepting complex or parallel work, flags when scope exceeds that limit, and
gives you clear options — sequence the work, reduce scope, or proceed with
a noted quality risk.

No silent degradation. Visible limits. Your decision.

---

## How To Activate It

Install the `SKILL.md` file into your Claude skills directory.

Once installed, Claude applies span assessment automatically when parallel
or high-complexity tasks are requested.

You can invoke it directly:

> "Before you take this on, assess your span of control."

Or for large parallel requests:

> "Is this within your reliable operating range? Flag it if not."

---

## What You'll See

For tasks clearly within reliable span — nothing. Claude executes.

When span is a genuine factor:

```
📊 Span of Control Assessment

Requested Scope: [what was asked]
Parallel Tasks: [count]
Complexity Level: [low / moderate / high / excessive]
Span Status: Within range / Approaching limit / Exceeds reliable limit

Recommendation:
  Option A — Sequential: [sequence proposed, quality maintained]
  Option B — Scoped parallel: [reduced scope, quality maintained]
  Option C — Full parallel as requested: [throughput achieved, quality risk noted]

Question: [how you want to proceed]
```

---

## The Three Span Dimensions Claude Assesses

**Parallel task count** — how many independent tasks can run simultaneously
at full quality. 1-2 is high reliability. 3-4 is manageable. 5+ recommends
sequential execution.

**Task complexity** — how much working context the task requires. Well-defined
tasks with clear contracts extend reliable span. Ambiguous high-complexity
tasks compress it.

**Coordination load** — how much overhead comes from managing multiple tools
or sub-processes simultaneously.

---

## What Changes In Claude's Behavior

| Without This Skill | With This Skill |
|---|---|
| Accepts any scope without assessment | Assesses span before accepting |
| Quality degrades silently at scale | Span limits visible before execution |
| Throughput prioritized over reliability | Quality over throughput — always |
| User discovers degradation in the output | User informed before execution begins |
| No options offered when limit exceeded | Clear options presented for user decision |

---

## The Key Insight

Structure extends span. A well-contracted task with clear criteria requires
less active tracking than an ambiguous one. The more you define upfront —
using `contract-first-decomposition` — the more Claude can reliably handle
in parallel.

Invest in structure, get more reliable throughput. That's the trade.

---

## Tips

- For large parallel requests, leading with: "Here are 5 tasks — which can
  run in parallel and which should be sequenced?" gives Claude a chance to
  assess and structure before diving in.
- If Claude flags span limits and you need the full scope done, ask: "What's
  the best sequence to get all of this done reliably?" Claude will prioritize
  and sequence accordingly.
- In long working sessions, Claude may recalibrate span as context accumulates.
  That's normal — it means the skill is actively monitoring, not failing.

---

## How It Works With Other Skills

- **contract-first-decomposition** — good contracts increase reliable span
- **monitoring-protocol** — at span edges, monitoring level increases to catch quality degradation early
- **adaptive-coordination** — handles corrective response when scope expands beyond span mid-task
- **verifiable-completion** — stricter verification applied when span is stretched
- **human-in-loop-escalation** — escalates when user insists on scope that clearly exceeds reliable limit

---

## Source

This skill is built on research from:
> Tomašev, N., Franklin, M., & Osindero, S. (2026). *Intelligent AI Delegation.*
> Google DeepMind.

Structured and formatted by **YVYC (Your Vision Your Creation).**
Licensed under **CC BY 4.0** — free to use, share, and adapt with attribution.

🌐 [yourvisionyourcreation.com](https://www.yourvisionyourcreation.com)
🐙 [github.com/Forexgod21](https://github.com/Forexgod21)
