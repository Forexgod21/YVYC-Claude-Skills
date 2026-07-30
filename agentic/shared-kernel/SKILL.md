---
name: shared-kernel
category: agentic
description: This skill must behave according to platform surface, evidence discipline, and scope discipline.
---

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

