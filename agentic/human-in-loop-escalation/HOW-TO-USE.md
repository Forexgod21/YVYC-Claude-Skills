# HOW TO USE — human-in-loop-escalation

**Category:** Agentic
**Skill Version:** 1.0
**Author:** YVYC (Your Vision Your Creation)

---

## What This Skill Does

This skill gives Claude a clear decision tree for when to stop and require
your input during task execution.

Not every decision escalates — that would be useless. But specific triggers
always do. Claude knows the difference, stops at the right moments, gives you
everything you need to decide quickly, and waits for your direction before
continuing.

You stay meaningfully in control. Not nominally. Meaningfully.

---

## The Problem It Solves

An AI with broad autonomy will eventually hit a moment where continuing without
human input is the wrong call. An irreversible action not explicitly authorized.
A decision outside the original scope. An ethical concern requiring human
judgment.

Without this skill, Claude may try to resolve it alone — self-authorizing past
its scope, making judgment calls it wasn't cleared to make.

**human-in-loop-escalation** stops that. Claude knows exactly when to stop,
what to report, and how to wait productively until you respond.

---

## How To Activate It

Install the `SKILL.md` file into your Claude skills directory.

Once installed, Claude applies the escalation decision tree automatically
throughout task execution.

You can also set escalation sensitivity explicitly:

> "Escalate anything that feels outside the original scope — don't try to
> resolve it yourself."

Or reduce unnecessary escalation:

> "You have my authorization for all reversible decisions in this task —
> only escalate if something is irreversible or an ethical concern."

---

## What You'll See

When Claude escalates:

```
🛑 Escalation Required — Human Input Needed

Trigger: [what caused the escalation]
Trigger Type: [mandatory / discretionary]
Situation: [full context]
Decision Required: [the specific decision needed]
Options:
  A: [option and consequences]
  B: [option and consequences]
  C: [stop entirely]
Claude's Recommendation: [if applicable]
Task State: [what is safe to continue while waiting]
```

Claude does not proceed until you respond with explicit direction.

---

## Mandatory Escalation Triggers — Claude Always Stops

These always trigger escalation, no exceptions:

- **Irreversibility threshold** — action cannot be undone and wasn't pre-authorized
- **Scope breach** — decision falls outside the original delegated task
- **Ethical concern** — harm to third parties, legal risk, privacy violation
- **Confidence failure** — confidence dropped below what the task's stakes require
- **Security or safety flag** — anomalous behavior or risk detected
- **Conflicting instructions** — contradictory instructions from different sources
- **Novel situation** — unanticipated situation Claude cannot resolve within scope

## Discretionary Triggers — Claude Uses Judgment

These may escalate depending on context:

- Resource consumption significantly exceeding estimates
- Intermediate results substantially different from expected
- Third party interests affected in unexpected ways
- Task complexity significantly higher than assessed

---

## What Changes In Claude's Behavior

| Without This Skill | With This Skill |
|---|---|
| May self-authorize past scope limits | Stops at mandatory triggers, no exceptions |
| Escalates after acting when it should have been before | Escalates before taking the triggering action |
| Incomplete situation report when stopping | Full report with options and consequences |
| Resumes based on probable user intent | Resumes only on explicit human authorization |
| Escalation feels like failure | Escalation treated as correct behavior |

---

## What Claude Does While Waiting

Claude doesn't just freeze. While waiting for your response:
- Documents complete task state at the escalation point
- Identifies any sub-tasks safe to continue without touching the escalated decision
- Prepares information needed once you respond

It does not touch the escalated decision path until you authorize it.

---

## Tips

- When you receive an escalation report, your three real options are always:
  authorize one of the options Claude presented, redirect entirely, or stop.
- If Claude escalates on something you consider within its authorized scope,
  say: "You're authorized for this — proceed." Claude will document it and
  continue.
- For long autonomous tasks, define escalation boundaries upfront in your
  task contract: "Escalate if X, Y, or Z. You have standing authorization
  for everything else."

---

## How It Works With Other Skills

- **reversibility-gate** — irreversible, unauthorized actions trigger mandatory escalation
- **adaptive-coordination** — when it can't resolve mid-task disruption within scope, escalation takes over
- **monitoring-protocol** — detection layer that identifies conditions triggering escalation
- **trust-calibration** — confidence failures trigger discretionary or mandatory escalation
- **zone-of-indifference-override** — out-of-scope situations route to this skill for response

---

## Source

This skill is built on research from:
> Tomašev, N., Franklin, M., & Osindero, S. (2026). *Intelligent AI Delegation.*
> Google DeepMind.

Structured and formatted by **YVYC (Your Vision Your Creation).**
Licensed under **CC BY 4.0** — free to use, share, and adapt with attribution.

🌐 [yourvisionyourcreation.com](https://www.yourvisionyourcreation.com)
🐙 [github.com/Forexgod21](https://github.com/Forexgod21)
