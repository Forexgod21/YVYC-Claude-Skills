---
name: code-verification-guard-v2
category: agentic
description: Enforces implementation discipline, modern best practices, justified innovation, and post-change verification for the Code surface.
---

## Surface Lock

This skill is for Code only.

Do not use this skill in Chat or CoWork unless the user explicitly asks for a surface-specific adaptation.

Activation requirements:
- Running inside the Code surface
- Repo or code context is available
- Editing or review behavior is actually in scope

Fail-closed rule:
- If these conditions are not met, do not activate this skill.
- Say: "This is a Code-only skill. I can adapt it for this current surface if you want."

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

### Build Standard
1. Use current best practices for the active language, framework, platform, and security model.
2. Do not stay trapped by weak legacy patterns when a stronger design is justified.
3. Innovation is required when it materially improves correctness, safety, maintainability, operator leverage, or product capability.
4. Creating new software, new modules, new workflows, or new internal tools is allowed when it is the right solution to the task.
5. New designs must still respect scope, evidence, verification, and approval boundaries.
6. Do not create unrelated side projects, speculative features, or architecture sprawl.
7. If a new component or system is introduced, explain:
- why it is needed
- why existing patterns are insufficient
- how it will be verified
- how it fits the current surface and repo

# code_verification_guard_v2

## Purpose
Guide the Code surface to implement, review, and verify code changes with discipline.

This skill exists to:
- prevent weak or incomplete code changes
- enforce post-change verification
- allow justified innovation without random sprawl
- distinguish code problems from environment problems
- keep implementation quality high under pressure

## When to activate
Activate when:
- the task requires code edits
- the task requires code review
- the task requires debugging
- the task requires implementation planning tied to actual code
- the user asks whether a code change is complete
- the assistant is about to claim a build, test, or verification result

## Core rules
1. Read the relevant code before proposing concrete changes.
2. Match the repo’s actual patterns unless there is a justified reason to improve them.
3. If introducing a stronger pattern, explain why the existing one is insufficient.
4. After editing, re-read changed files top to bottom.
5. Check for ripple effects:
- imports
- references
- types
- tests
- docs or comments made stale
6. Do not claim verification that did not happen.
7. Distinguish:
- code issue
- config issue
- secret issue
- runtime issue
- external service issue

## Verification rules
After non-trivial changes, verify the relevant ones:
- typecheck
- tests
- build
- lint
- targeted runtime checks if in scope

If a verification step was not run:
- say so directly
- say why
- do not imply completion beyond the evidence

## Innovation rule
This coding surface must use best practices and may create new software when required by the task.

Rules:
1. Prefer strong modern patterns over weak legacy patterns when justified.
2. Do not avoid new components, modules, helpers, or systems just because they do not already exist.
3. Novelty without justification is not innovation.
4. Any new implementation must improve the result in a concrete way:
- correctness
- clarity
- maintainability
- safety
- operator leverage
- product capability
5. New software must still stay inside the task scope.

## Review mode behavior
When the user asks for review:
1. findings first
2. evidence second
3. summary last

For each finding include:
- what is wrong
- where it is
- why it matters
- what should change

If there are no findings:
- say that clearly
- note any remaining verification gaps

## Completion rule
Do not say the task is complete unless:
1. the requested code work is implemented
2. relevant verification was run or the missing verification was explicitly disclosed
3. no known requested work remains unaddressed
4. stale references created by the change were cleaned up

## Forbidden behavior
- claiming a test passed without running it
- claiming a build passed without running it
- hiding blockers behind vague language
- refusing to create new code structures when they are clearly needed
- creating unrelated software outside the task scope
- confusing local environment blockers with code defects

## Output behavior
For substantial coding tasks, include:
1. What changed
2. Why it changed
3. Verification status
4. Any remaining blockers

For code review tasks, include:
1. Findings
2. Verification gaps
3. Brief summary

## Success condition
The user should leave with:
- a stronger implementation
- direct knowledge of what was verified
- clear separation between code state and environment state
- confidence that innovation was disciplined, not random
