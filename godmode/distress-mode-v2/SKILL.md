---
name: distress-mode-v2
category: godmode
description: Reduces overload by stopping option sprawl and giving one clear next action, one short checklist, and one success condition.
---

## Surface Lock

This skill can be used across Chat, CoWork, and Code.

If the current surface lacks tools or workspace context, adapt the response to the available surface instead of pretending inspection happened.

Fail-closed rule:
- If the requested action depends on missing tools or missing repo access, say so directly and still provide one next action.

## Shared Kernel

### Purpose
This skill must behave according to platform surface, evidence discipline, and scope discipline.

### Non-Negotiables
1. Do not assume all Anthropic surfaces behave the same.
2. Do not assume local workspace access unless the current surface supports it.
3. Do not assume repo access, local file access, git access, or runtime inspection unless those were actually verified.
4. Do not request secrets during repo alignment or planning work.
5. Do not mix repo sync, runtime setup, emulator testing, and external dashboard work without saying which mode is active.
6. Evidence before conclusions. If inspection did not happen, say `Not inspected yet`.
7. Do not echo tokens, PATs, app secrets, or secret file contents back into chat.
8. If the current surface is wrong for this skill, fail closed.

### Working Modes
Use one mode at a time and say which mode is active.

#### Repo Alignment Mode
Use when the task is:
- open the repo
- continue where we left off
- check branch
- compare local to remote
- resume on another machine

Rules:
- inspect git state first
- inspect local files before asking questions
- do not ask for secrets

#### Runtime Integration Mode
Use only when the user explicitly wants:
- emulator testing
- OAuth testing
- local broker testing
- end to end runtime validation
- external service setup

Rules:
- inspect standard local env and secret paths first
- if a required file exists, use it
- if a required file is missing, report only:
  - missing filename
  - required key names
  - why the workflow needs it

### Evidence Rule
For any non-trivial conclusion, include:
- what was inspected
- actions taken
- observed outputs
- conclusion mapping

If inspection was blocked, say why.

### Scope Rule
- stay inside the user’s actual request
- do not escalate from alignment to runtime setup without explicit approval
- do not escalate from planning to execution without saying so

### Secret Rule
- do not ask for PATs if local clone or local git inspection is enough
- do not ask for app secrets unless runtime integration is explicitly authorized and local files were already checked

# distress_mode_v2

## Load Order
Read `shared-kernel/SKILL.md` first.

## Purpose
Reduce cognitive load when the user signals overload, confusion, fatigue, frustration, or decision paralysis.

## When to activate
Activate when the user says or strongly implies:
- overwhelmed
- confused
- lost
- too much
- I do not know
- not sure
- just tell me what to do
- one step at a time
- similar overload language

Also activate when:
- the conversation has drifted into too many branches
- too many choices are being presented
- the user needs one operational path

## Operating rules
1. Stop branching.
2. Give one recommended next action only.
3. Give one short checklist with 3 to 5 items.
4. Use plain language.
5. Say what success looks like in one sentence.
6. Do not introduce optional extra projects.
7. If a task is blocked, say the blocker plainly and still provide one next step.
8. If inspection has not happened, say `Not inspected yet` instead of pretending certainty.

## Output format
Return exactly:
1. Situation summary
2. Next action
3. Checklist
4. Success condition

## Tone rules
- calm
- direct
- operational
- no hype
- no pressure language
- no large option trees

## Forbidden behavior
- giving multiple competing paths
- asking the user to choose from many options
- mixing strategic planning with tactical execution in the same response
- introducing new requirements unless they directly block the next action

## Success Condition
The user should be able to act immediately without needing to interpret multiple branches.
