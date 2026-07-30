---
name: retry-recovery-budget
version: 1.0
author: YourVisionYourCreation LLC
license: CC BY 4.0
category: agentic
description: >
  Activate whenever an agent encounters a failed tool call, a failed
  action, an unexpected result, or an error of any kind during task
  execution. Governs how many retries are permitted, what must change
  between attempts, when to escalate to the operator, and how failures
  are recorded. Prevents infinite retry loops, silent failure
  swallowing, and unstructured error handling.
---

# Retry Recovery Budget

## Attribution

Built and documented by YourVisionYourCreation LLC (YVYC).
Original synthesis of publicly established agent reliability patterns.
Attribution: YourVisionYourCreation LLC, yourvisionyourcreation.com

## Doctrine Statement

An agent that retries without a budget is an agent that has replaced
judgment with hope. Every retry costs tokens, time, and operator trust.
Every silent failure hides information the operator needed. This skill
converts failure from an event the agent reacts to into a resource the
agent spends deliberately.

The core rule: retries are a budget, not a reflex. The budget is set
before execution begins, spent with a reason attached to every attempt,
and closed out with a report whether the task succeeded or failed.

## The Universal So-What

Without this skill, agents burn context windows on identical retries,
mask the true failure point, and surface errors to the operator only
after the damage compounds. With it, every failure produces one of three
defined outcomes: a corrected retry, a controlled fallback, or a clean
escalation. Nothing else is permitted.

## Operating Rules

### Rule 1: Budget Before Execution

Before any multi-step task begins, the agent declares a retry budget.
The budget is stated, not assumed, and it is stated in terms of the four
failure classes below. A task that begins without a declared budget
operates at the default ceilings and says so.

### Rule 2: Classify Before Retrying

No retry fires before the failure is classified. Classification is the
gate; the budget is what the gate spends.

| Class | Meaning | Ceiling | Required behavior |
|---|---|---|---|
| Transient | Environment hiccup, timeout, rate limit | 3 | Retry with backoff, unchanged call permitted |
| Structural | The action itself was malformed | 1 | Fix the defect first, then one retry |
| Boundary | Permissions or policy said no | 0 | Immediate escalation, no retry |
| Unknown | Cause cannot be determined | 1 | One diagnostic attempt, then escalate |

### Rule 3: Zero Retries on Boundary Failures

This rule has no exceptions and no operator override at task level. An
agent that retries a permission denial is an agent probing a security
boundary. Whether the intent is benign is beside the point; the behavior
pattern is indistinguishable from an attack and is prohibited by rule.

Boundary failures escalate on the first occurrence with the denial
recorded verbatim.

### Rule 4: Something Must Change Between Attempts

Except for the transient class, where backoff is itself the change, no
retry is permitted unless the agent can state what is different about
this attempt. "Trying again" is not a change. If nothing can be changed,
the budget is not spent; the failure escalates.

### Rule 5: Verbatim Error Records Only

Failures are recorded as received, not as understood. The agent captures
the exact error text, the exact call that produced it, and the exact
inputs. Paraphrased errors destroy the operator's ability to diagnose and
are prohibited.

The record structure per attempt:

```
ATTEMPT   [n of ceiling]
ACTION    [the exact call]
INPUT     [the exact parameters]
ERROR     [verbatim, unedited]
CLASS     [transient | structural | boundary | unknown]
CHANGED   [what is different from the prior attempt]
BUDGET    [remaining in this class]
DECISION  [retry | fallback | escalate]
```

### Rule 6: Exhaustion Is a Full Stop

When a budget is exhausted, the agent halts that line of work. It does
not reclassify the failure into a class with remaining budget, and it
does not continue past the failed step hoping later steps compensate.
Reclassification to buy retries is the loophole this rule closes.

### Rule 7: Escalation Carries Work Forward

An escalation is a handoff, not an abandonment. Every escalation
includes:

- The verbatim failure records for all attempts
- What was completed before the failure, in a recoverable state
- The agent's classification and why
- One recommended next action, not a menu of options

### Rule 8: No Silent Swallowing

A failure that was recovered from is still reported. The operator learns
about every failure at close-out even when the task succeeded. Successful
recovery is information about system fragility and belongs in the record.

## Fallback Discipline

A fallback is a different path to the same requirement, not a lowered
requirement. Before taking a fallback the agent confirms two things: the
fallback satisfies the original requirement, and the operator would
recognize it as the same task. If either fails, the fallback becomes an
escalation.

Silently substituting a lesser outcome is the most damaging form of this
failure because it arrives labeled as success.

## Cross-Step Budget Accounting

Budgets are held per class per task, not per call. An agent that spends
three transient retries on step one does not arrive at step four with a
fresh three. When a task is failing broadly, the budget structure is what
makes that visible early rather than at the end.

## Interaction With Operator Authority

The operator may raise or lower any ceiling at task start, with one
exception: the boundary class stays at zero. Requests to raise it are
declined with the reason stated, which is itself an escalation event.

## Adversarial Evaluator Gate

Before closing any task that involved a failure, the agent runs this
check:

> If a hostile reviewer wanted to prove this agent hid a failure, where
> would they look first?

The answer names the weakest point in the record. That point gets a
complete record or an explicit acknowledgment of the gap before
close-out. A failure record that cannot survive this question is not
finished.

## Failure Modes This Skill Closes

| Failure mode | What it looks like | What this skill requires instead |
|---|---|---|
| Retry loop | Same call, five times, identical error | Ceiling by class, change required per attempt |
| Boundary probing | Retrying a permission denial | Zero retries, first-occurrence escalation |
| Paraphrased errors | "It seems the API had an issue" | Verbatim error text |
| Silent swallow | Recovered failure never reported | All failures reported at close-out |
| Reclassification | Moving a boundary failure to unknown for budget | Exhaustion is a full stop |
| Fallback drift | Lesser outcome reported as success | Fallback must satisfy the original requirement |

## Pairs Well With

- `monitoring-protocol` for full-session observability
- `agent-observability-doctrine` for the record structure these logs
  write into
- `human-in-loop-escalation` for the handoff when budgets exhaust
- `verifiable-completion` to confirm no failed step was silently skipped
  at close-out
- `permission-attenuation` for why boundary failures are structural, not
  incidental

---

*YourVisionYourCreation LLC, yourvisionyourcreation.com*
*Licensed under CC BY 4.0*
