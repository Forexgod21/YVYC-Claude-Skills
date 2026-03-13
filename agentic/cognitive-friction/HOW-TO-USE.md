# HOW TO USE — cognitive-friction

**Category:** Agentic
**Skill Version:** 1.0
**Author:** YVYC (Your Vision Your Creation)

---

## What This Skill Does

This skill teaches Claude when to slow down.

Not everything deserves the same speed. Routine tasks execute fast. High-stakes
decisions get a deliberate pause — Claude surfaces what it is about to do, names
the risk, and gives you a moment to engage before it proceeds.

The friction scales with the situation. Low stakes — no interruption. High stakes
— full pause.

---

## The Problem It Solves

AI moving fast is usually good. But fast execution on a decision you didn't fully
think through is how mistakes happen at scale.

Without this skill, Claude applies the same speed to everything — a quick draft
gets the same energy as a high-stakes financial decision. That's dangerous.

**cognitive-friction** reads the situation and adjusts. It slows Claude down
exactly when slowing down is the right call, and stays out of the way when it
isn't.

---

## How To Activate It

Install the `SKILL.md` file into your Claude skills directory.

Once installed, Claude applies friction calibration automatically. It runs in
the background and only surfaces when the stakes warrant it.

You can also invoke it directly:

> "Before you proceed, slow down and tell me what you're assuming."

Or:

> "Use cognitive-friction on this — I want to think through it first."

---

## What You'll See

For routine tasks — nothing. Claude just executes.

For light friction — a brief inline note:
> "I'm assuming you want X here — proceeding on that basis."

For medium to heavy friction — a deliberate pause:

```
⏸ Pause — This decision deserves a moment.

Situation: [what Claude understands is being asked]
Assumption: [what Claude is assuming]
Risk: [specific risk if wrong]
Question: [the one thing Claude needs confirmed]
```

For maximum friction — hands off to reversibility-gate for full confirmation.

---

## What Changes In Claude's Behavior

| Without This Skill | With This Skill |
|---|---|
| Same speed regardless of stakes | Speed scales with actual stakes |
| Assumptions made silently | Key assumptions surfaced before proceeding |
| Risks not named until after the fact | Risks named at the decision point |
| User must catch high-stakes moments themselves | Claude flags them automatically |
| Over-caution on everything or nothing | Calibrated — friction only where it belongs |

---

## The Friction Scale At A Glance

| Stakes | Uncertainty | What Happens |
|---|---|---|
| Low | Low | Claude executes directly |
| Low | Moderate | Brief assumption note, proceed |
| Moderate | Moderate | Surfaces assumptions, asks one question |
| High | Any | Full pause — risk named, confirmation required |
| High + Irreversible | Any | Hard stop via reversibility-gate |

---

## How It Works With Other Skills

This skill is part of a three-skill safety layer:

- **cognitive-friction** — flags the moment and creates the pause
- **reversibility-gate** — handles the hard stop for irreversible actions
- **trust-calibration** — surfaces Claude's actual confidence when uncertainty
  is driving the friction

Together they cover planning, execution, and knowledge reliability.

---

## Tips

- If Claude's friction feels unnecessary on something you've already thought
  through, just say "proceed" — Claude will move forward.
- If you want maximum friction on a specific task, say: "Pause and walk me
  through every assumption before you do anything."
- If you want Claude to run without friction for a session: "I've thought
  this through — execute without pausing unless something is irreversible."

---

## Source

This skill is built on research from:
> Tomašev, N., Franklin, M., & Osindero, S. (2026). *Intelligent AI Delegation.*
> Google DeepMind.

Structured and formatted by **YVYC (Your Vision Your Creation).**
Licensed under **CC BY 4.0** — free to use, share, and adapt with attribution.

🌐 [yourvisionyourcreation.com](https://www.yourvisionyourcreation.com)
🐙 [github.com/Forexgod21](https://github.com/Forexgod21)
