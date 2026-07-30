# How To Use: Retry Recovery Budget

**Category:** `agentic/` | **YVYC Original**

## What This Skill Does

It turns retries into a budget the agent spends deliberately instead of a
reflex it fires automatically. Every failure gets classified, every retry
costs something, and every failure reaches you in the record whether the
task recovered or not.

## Who This Is For

- Anyone running multi-step agentic tasks where tool calls can fail
- Developers building automation on the Claude API or Claude Code
- Operators who have watched an agent burn an entire context window
  retrying the same broken call
- Teams that need an audit trail of what failed and why

## Installation

1. Copy the `retry-recovery-budget` folder into your Claude skills
   directory.
2. Confirm both files are present: `SKILL.md` and `HOW-TO-USE.md`.
3. The skill activates automatically whenever the agent encounters a
   failed action, tool error, or unexpected result.

## What Changes in Practice

**Before this skill:**
Your agent hits a rate limit, retries five times in a row with no
changes, fills the context with identical errors, and either stalls or
reports vague failure at the end.

**After this skill:**
The agent classifies the failure as transient, retries up to three times
with backoff, logs each attempt in a structured record, and if the
ceiling is reached, stops and hands you a clean escalation with its work
preserved and one recommendation attached.

## The Four Failure Classes

| Class | Meaning | Agent behavior |
|---|---|---|
| Transient | Environment hiccup | Retry with backoff, ceiling of 3 |
| Structural | The action was malformed | Fix the defect first, then one retry |
| Boundary | Permissions or policy said no | Zero retries, immediate escalation |
| Unknown | Cause unclear | One diagnostic attempt, then escalate |

The boundary class is the one that protects you. An agent that retries
permission denials is an agent probing your security boundaries. This
skill makes that behavior impossible by rule, and the rule holds even if
you try to override it.

## Setting a Custom Budget

You can override the defaults at task start:

```
Run this pipeline. Retry budget: transient 5, structural 2,
everything else escalate immediately.
```

The agent will confirm the budget before execution and hold to it. The
boundary class stays at zero regardless of what you set; a request to
raise it is declined with the reason stated.

## Reading the Failure Records

Every failure produces a structured record:

```
ATTEMPT   2 of 3
ACTION    [the exact call]
INPUT     [the exact parameters]
ERROR     [verbatim, unedited]
CLASS     transient
CHANGED   backoff raised to 4s
BUDGET    1 remaining
DECISION  retry
```

These records are your audit trail. If a task partially fails, the
records tell you exactly where, why, and what was tried, with no digging.

The field to read first is CHANGED. If it says nothing changed, the
retry should not have fired.

## The Rule That Catches Hidden Failures

Failures are reported at close-out even when the task succeeded. If the
agent recovered from three transient errors on the way to a clean result,
you still see all three. Successful recovery tells you where the system
is fragile, and that information belongs to you, not to the agent's
internal state.

## Budgets Do Not Reset Per Step

Three transient retries spent on step one means step four does not arrive
with a fresh three. Budgets are held per class across the whole task. This
is deliberate: a task failing broadly becomes visible early instead of at
the end.

## On Fallbacks

A fallback is a different path to the same requirement, never a lowered
requirement. If the agent cannot reach your original outcome, it escalates
rather than delivering something lesser labeled as success. That
substitution is the most damaging failure mode in agentic work because it
arrives looking like a win.

## Pairs Well With

- `monitoring-protocol` for full-session observability
- `agent-observability-doctrine` for the record structure these logs
  write into
- `human-in-loop-escalation` for the handoff when budgets exhaust
- `verifiable-completion` to confirm no failed step was silently skipped
  at close-out

## What This Skill Will Refuse

- Retrying a permission denial, under any instruction
- Retrying without stating what changed
- Paraphrasing an error instead of quoting it
- Reclassifying a failure to buy more retry budget
- Continuing past a failed step hoping later steps compensate
- Closing a task without reporting failures that were recovered from

## Attribution

Built and documented by YourVisionYourCreation LLC.
yourvisionyourcreation.com

---

*Licensed under CC BY 4.0*
