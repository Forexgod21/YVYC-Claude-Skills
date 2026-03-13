# HOW TO USE — multi-objective-tradeoff

**Category:** Agentic
**Skill Version:** 1.0
**Author:** YVYC (Your Vision Your Creation)

---

## What This Skill Does

When a task has competing objectives, this skill stops Claude from making a
silent values call on your behalf.

Claude surfaces the conflict, names exactly what is gained and lost under each
option, and lets you decide the priority before executing. Your values drive
the output — not Claude's assumption about what you probably value.

---

## The Problem It Solves

Most real tasks have more than one goal. And most goals, pushed far enough,
conflict. Fast vs. thorough. Cheap vs. quality. Safe vs. decisive.

Without this skill, Claude picks one silently and executes. You get the output
and only then discover it was optimized for the wrong thing.

**multi-objective-tradeoff** catches the conflict before execution. You see
the tradeoff, set the priority, and Claude executes against what you actually
decided — not what it assumed.

---

## How To Activate It

Install the `SKILL.md` file into your Claude skills directory.

Once installed, Claude applies conflict detection automatically when multiple
objectives are present.

You can also invoke it directly:

> "Before you start, identify any competing objectives and surface the tradeoffs."

Or mid-task:

> "These goals might conflict — use multi-objective-tradeoff and show me
> what I'm trading off."

---

## What You'll See

When competing objectives are detected:

```
⚖️ Competing Objectives Detected

Objective A: [first objective]
Objective B: [second objective]
Conflict: [specifically how they conflict]

Option 1 — Prioritize A:
  Gain: [what you get]
  Cost: [what you give up]

Option 2 — Prioritize B:
  Gain: [what you get]
  Cost: [what you give up]

Option 3 — Balanced approach:
  Gain: [partial optimization on both]
  Cost: [neither fully met]

Claude's Recommendation: [if one option is clearly stronger]
Question: [the one thing needed to set priority]
```

For simple two-way conflicts:
> "These two goals conflict — [A] vs. [B]. Which matters more here?"

---

## Common Conflict Patterns Claude Watches For

- **Speed vs. Quality** — "Do this fast and make it excellent"
- **Scope vs. Focus** — "Be comprehensive but keep it concise"
- **Safety vs. Decisiveness** — "Be careful but don't slow us down"
- **Short-term vs. Long-term** — quick fix now vs. correct fix later
- **User preference vs. Best practice** — you want X, best practice says Y
- **Transparency vs. Simplicity** — full detail vs. clean summary
- **Cost vs. Capability** — cheap solution vs. better solution

---

## What Changes In Claude's Behavior

| Without This Skill | With This Skill |
|---|---|
| Silent judgment call on competing goals | Conflict surfaced before execution |
| Output optimized for assumed priority | Output optimized for your stated priority |
| Vague acknowledgment of tradeoffs | Specific gains and costs named for each option |
| Values decision made by Claude | Values decision made by you |
| Priority discovered after the fact | Priority confirmed before work begins |

---

## After You Set the Priority

Once you confirm, Claude:
- Documents the priority hierarchy
- Executes consistently against it throughout the task
- Notes any point where the hierarchy produces a significant consequence
  you should be aware of
- Does not re-open the decision unless new information materially changes it

---

## Tips

- If you've already thought through the tradeoff and know what you want,
  just say so upfront: "Prioritize quality over speed on this one." Claude
  documents it and executes accordingly.
- If Claude presents a tradeoff and one option is clearly right for your
  situation, pick it and move on. The surface is there so you can decide —
  not to create friction for its own sake.
- Pair this with `contract-first-decomposition` — define the priority
  hierarchy in the Pre-Task Contract so it's locked in before any
  execution begins.

---

## How It Works With Other Skills

- **contract-first-decomposition** — captures priority hierarchy in the task contract before execution
- **principal-agent-alignment** — catches drift when competing objectives pull interpretation away from intent
- **cognitive-friction** — slows down on high-stakes tradeoffs that deserve deliberate thought
- **human-in-loop-escalation** — escalates when conflicts involve ethical or values questions beyond task scope

---

## Source

This skill is built on research from:
> Tomašev, N., Franklin, M., & Osindero, S. (2026). *Intelligent AI Delegation.*
> Google DeepMind.

Structured and formatted by **YVYC (Your Vision Your Creation).**
Licensed under **CC BY 4.0** — free to use, share, and adapt with attribution.

🌐 [yourvisionyourcreation.com](https://www.yourvisionyourcreation.com)
🐙 [github.com/Forexgod21](https://github.com/Forexgod21)
