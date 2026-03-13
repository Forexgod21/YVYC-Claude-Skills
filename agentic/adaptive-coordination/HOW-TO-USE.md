# HOW TO USE — adaptive-coordination

**Category:** Agentic
**Skill Version:** 1.0
**Author:** YVYC (Your Vision Your Creation)

---

## What This Skill Does

This skill teaches Claude how to handle disruption mid-task — cleanly, transparently,
and without making things worse.

When something fails, changes, or goes sideways during execution, Claude runs a
disciplined diagnostic cycle: detect the trigger, diagnose the cause, assess
urgency and reversibility, select the right response, and report what changed.

No silent pivots. No automatic retries that compound a problem. No continuing
as if nothing happened.

---

## The Problem It Solves

Tasks don't always go as planned. Tools fail. Conditions change. The user shifts
direction. A result comes back wrong.

Without this skill, Claude may silently adjust its approach, keep retrying a
failed step, or continue down a path that no longer matches what was intended.
By the time the problem surfaces, it's larger than it needed to be.

**adaptive-coordination** catches disruption at the moment it happens, names it,
and responds correctly before the problem compounds.

---

## How To Activate It

Install the `SKILL.md` file into your Claude skills directory.

Once installed, Claude applies adaptive coordination automatically when disruption
is detected during task execution.

You can also invoke it directly:

> "Something changed — use adaptive-coordination to reassess before continuing."

Or:

> "That step failed — diagnose and tell me what the corrective response is."

---

## What You'll See

For minor adjustments — a brief inline note:
> "Tool returned an error — switching to alternative approach, continuing."

For significant disruptions:

```
⚡ Adaptive Coordination Triggered

Trigger: [what was detected]
Root Cause: [diagnosis]
Reversibility: [reversible / irreversible]
Urgency: [low / medium / high]
Selected Response: [what Claude is doing]
Impact on Task: [how this changes the plan]
Next Step: [what happens next]
```

---

## What Changes In Claude's Behavior

| Without This Skill | With This Skill |
|---|---|
| May silently pivot approach mid-task | Names every trigger before responding |
| May retry failed steps automatically | One retry allowed, then surfaces and reports |
| Continues after irreversible failures | Stops immediately and escalates |
| Scope changes absorbed without acknowledgment | Scope changes surfaced and confirmed |
| User discovers problems at the end | User informed at the moment disruption occurs |

---

## The Response Decision At A Glance

| What Happened | What Claude Does |
|---|---|
| Minor issue, reversible | Adjust and continue |
| Sub-task failed, reversible | Retry once, report if fails again |
| User changed scope | Re-state criteria, confirm, continue |
| Tool unavailable | Propose alternative, wait for confirmation |
| Verification failed | Return to failed step, diagnose, retry |
| High urgency situation | Pause and escalate to user |
| Irreversible action failed | Stop immediately, full report, await instruction |
| Security concern detected | Stop, report, require human authorization |

---

## How It Works With Other Skills

**contract-first-decomposition** — the original plan. Adaptive coordination
reports deviations from it.

**reversibility-gate** — when the adaptive response involves an irreversible
action, reversibility-gate governs confirmation.

**verifiable-completion** — after any adaptive response, completion criteria
are re-verified against the updated task state.

**human-in-loop-escalation** — when the situation exceeds Claude's autonomous
response authority, that skill defines the escalation path.

---

## Tips

- If Claude surfaces an adaptive coordination trigger and you want it to proceed
  without pausing, say: "Understood — continue with your selected response."
- If the trigger changes what you actually need, this is the moment to redirect:
  "Given that, let's change course to X instead."
- For long complex tasks, expect adaptive coordination to activate at least once.
  That's normal — it means Claude is paying attention, not failing.

---

## Source

This skill is built on research from:
> Tomašev, N., Franklin, M., & Osindero, S. (2026). *Intelligent AI Delegation.*
> Google DeepMind.

Structured and formatted by **YVYC (Your Vision Your Creation).**
Licensed under **CC BY 4.0** — free to use, share, and adapt with attribution.

🌐 [yourvisionyourcreation.com](https://www.yourvisionyourcreation.com)
🐙 [github.com/Forexgod21](https://github.com/Forexgod21)
