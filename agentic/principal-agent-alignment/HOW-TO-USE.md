# HOW TO USE — principal-agent-alignment

**Category:** Agentic
**Skill Version:** 1.0
**Author:** YVYC (Your Vision Your Creation)

---

## What This Skill Does

This skill keeps Claude's interpretation of your task aligned with what you
actually need — throughout execution, not just at the start.

When Claude detects that its current path has drifted from your original intent,
it surfaces that drift immediately and asks one focused question to get back on
track. You never receive an output and think "that's not what I meant."

---

## The Problem It Solves

There is always a gap between what gets typed and what is actually meant. Claude
forms an interpretation, starts executing, and that interpretation can quietly
drift — assumptions compound, scope shifts, new information changes the context.

Without this skill, Claude delivers the output it interpreted you wanted.
With this skill, Claude continuously checks whether that interpretation is still
right — and surfaces it when it isn't.

---

## How To Activate It

Install the `SKILL.md` file into your Claude skills directory.

Once installed, Claude applies alignment discipline automatically throughout
task execution.

You can also invoke it directly:

> "Check your alignment — is what you're doing still what I actually need?"

Or mid-task:

> "Before you continue, tell me what you think my actual goal is here."

---

## What You'll See

When Claude makes a significant interpretive decision mid-task:
> "Interpreting this as [X] rather than [Y] — continuing on that basis.
> Let me know if that's not right."

When alignment drift is detected:

```
🎯 Alignment Check

Original Intent: [Claude's understanding of what you actually need]
Current Path: [what Claude is executing toward]
Drift Detected: [how the current path differs]
Interpretive Decision: [the specific interpretation that may be wrong]
Question: [the one thing that resolves the uncertainty]
```

---

## What Changes In Claude's Behavior

| Without This Skill | With This Skill |
|---|---|
| Executes to completion on initial interpretation | Checks alignment throughout execution |
| Optimizes for literal instruction | Serves actual intent when the two differ |
| Significant interpretive decisions made silently | Interpretive decisions named explicitly |
| Drift discovered at output delivery | Drift caught and surfaced mid-execution |
| User must catch misalignment themselves | Claude surfaces it proactively |

---

## The Six Drift Signals Claude Watches For

- **Scope drift** — current sub-task feels disconnected from original goal
- **Assumption drift** — early assumption is now questionable
- **Direction drift** — output growing in an unrequested direction
- **Context drift** — new information changes what you probably actually need
- **Metric drift** — optimizing for stated metric rather than actual goal
- **Priority drift** — your language or tone has shifted mid-task

---

## Tips

- If Claude surfaces an alignment check and you're still on track, say:
  "Still aligned — continue."
- If the drift Claude detected is real, this is your moment to redirect
  cleanly before more work goes in the wrong direction.
- For high-stakes tasks, you can request an explicit alignment check at
  any point: "Stop and confirm — what do you think my actual goal is?"
- Pair this with `contract-first-decomposition` — the Pre-Task Contract
  gives Claude a clear reference point for alignment checks throughout.

---

## How It Works With Other Skills

- **contract-first-decomposition** — original intent reference point
- **monitoring-protocol** — detects drift signals during execution
- **adaptive-coordination** — governs the corrective response when drift requires a course change
- **trust-calibration** — surfaces uncertainty when Claude's interpretation confidence is low
- **zone-of-indifference-override** — triggers when intent is ambiguous and automatic compliance would be wrong

---

## Source

This skill is built on research from:
> Tomašev, N., Franklin, M., & Osindero, S. (2026). *Intelligent AI Delegation.*
> Google DeepMind.

Structured and formatted by **YVYC (Your Vision Your Creation).**
Licensed under **CC BY 4.0** — free to use, share, and adapt with attribution.

🌐 [yourvisionyourcreation.com](https://www.yourvisionyourcreation.com)
🐙 [github.com/Forexgod21](https://github.com/Forexgod21)
