# HOW TO USE — monitoring-protocol

**Category:** Agentic
**Skill Version:** 1.0
**Author:** YVYC (Your Vision Your Creation)

---

## What This Skill Does

This skill keeps Claude actively aware of what is happening during a task —
and surfaces what matters at the right moments, at the right depth.

Not constant status updates. Not silence until the end. Calibrated signals
that tell you when something is on track, when something has shifted, and
when you need to step in.

---

## The Problem It Solves

Long or complex tasks can drift. A step completes, looks fine, and quietly
sets up a problem three steps later. Without monitoring, that problem surfaces
at the end when it is expensive to fix.

**monitoring-protocol** catches drift early. Claude maintains active awareness
throughout execution and reports signals — not noise — at natural checkpoints
and whenever something meaningful changes.

---

## How To Activate It

Install the `SKILL.md` file into your Claude skills directory.

Once installed, Claude applies monitoring calibrated to the complexity of
each task automatically.

You can also set the level explicitly:

> "Monitor this at Level 2 — I want reasoning quality tracked."

Or request a full state report at any time:

> "Give me a full state report on where this task stands."

---

## The Four Monitoring Levels

| Level | What It Tracks | When Used |
|---|---|---|
| L0 — Operational | Tools, resources, execution errors | All monitored tasks — minimum baseline |
| L1 — Plan Alignment | Sub-task progress vs original plan | Multi-step tasks with defined contracts |
| L2 — Reasoning Quality | Assumption validity, confidence shifts | High-stakes or complex reasoning tasks |
| L3 — Full State | Everything — decisions, tools, deviations | Maximum autonomy or security-sensitive tasks |

---

## What You'll See

**Level 0 — only when something is abnormal:**
> "Tool call failed — switching to fallback, continuing."

**Level 1 — at natural checkpoints:**
```
📊 Plan Alignment Check

Checkpoint: [sub-task or boundary]
Status: On track / Deviation detected
Sub-tasks Complete: [n of n]
Current Output: [matches / does not match expected]
Next Sub-task: [what is coming next]
```

**Level 2 — when reasoning quality shifts:**
```
🔍 Reasoning Quality Signal

Location: [where in the task]
Signal: [what changed]
Assumption Shift: [if any]
Impact: [how this affects the path]
Recommended Action: [continue / adjust / escalate]
```

**Level 3 — on request or at defined interval:**
```
📋 Full Task State Report

Task / Contract / Sub-tasks / Decisions / Tools / Deviations / Current State / Confidence
```

---

## What Changes In Claude's Behavior

| Without This Skill | With This Skill |
|---|---|
| Silent execution until output is delivered | Active awareness throughout |
| Problems surface at the end | Drift detected and reported early |
| User has no visibility mid-task | Calibrated signals at natural checkpoints |
| Deviation held until task completion | Deviation reported immediately |
| User must ask for status | Status surfaces when it matters |

---

## Tips

- You can request a full state report at any point: "Where does this task
  stand right now?" Claude gives you the complete picture immediately.
- If monitoring signals feel like too much, say: "Drop to L0 — only flag
  me if something is actually wrong."
- If you're running a high-autonomy task and want maximum visibility, say:
  "Monitor at L3 throughout."
- Pair this with `contract-first-decomposition` — the contract defines what
  monitoring checks against.

---

## How It Works With Other Skills

- **contract-first-decomposition** — defines what monitoring tracks against
- **adaptive-coordination** — responds when monitoring detects deviation
- **trust-calibration** — surfaces confidence gaps detected at Level 2
- **verifiable-completion** — final checkpoint in the monitoring cycle
- **human-in-loop-escalation** — escalation path when monitoring flags a
  situation beyond Claude's autonomous authority

---

## Source

This skill is built on research from:
> Tomašev, N., Franklin, M., & Osindero, S. (2026). *Intelligent AI Delegation.*
> Google DeepMind.

Structured and formatted by **YVYC (Your Vision Your Creation).**
Licensed under **CC BY 4.0** — free to use, share, and adapt with attribution.

🌐 [yourvisionyourcreation.com](https://www.yourvisionyourcreation.com)
🐙 [github.com/Forexgod21](https://github.com/Forexgod21)
