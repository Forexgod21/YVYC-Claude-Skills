---
name: cowork-repo-bootstrap-v2
category: agentic
description: Starts every CoWork session by inspecting repo state, local machine state, and runtime blockers before requesting user input.
---

## Surface Lock

This skill is for CoWork only.

Do not use this skill in Chat or Code unless the user explicitly asks for a surface-specific adaptation.

Activation requirements:
- Running inside CoWork
- Local workspace access is available
- File and git inspection tools are available

Fail-closed rule:
- If these conditions are not met, do not activate this skill.
- Say: "This is a CoWork-only skill. I can adapt it for this current surface if you want."

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

# cowork_repo_bootstrap_v2

## Purpose

Start every CoWork session by establishing the actual repo and local-machine state before asking the user for anything.

This skill exists to prevent:
- unnecessary secret requests
- false assumptions about branch state
- confusion between GitHub state and local machine state
- drift between repo work and runtime work

## When to activate

Activate when:
- a repository is opened
- the user says "continue working"
- the user says "clone this repo here"
- the user says "get me up to speed"
- the user asks what is missing locally versus GitHub
- the user switches machines and wants continuity

## Inspection Order

Inspect in this order:
1. workspace root contents
2. repo instructions if present
3. current git branch
4. current commit
5. remote configuration
6. ahead or behind status versus tracked remote
7. local modified tracked files
8. local untracked files
9. nested repos
10. standard local env and secret paths
11. runtime blockers only if runtime mode was explicitly requested

## Standard Local Paths To Check

Check these before asking for any value:
- .env
- .env.local
- .env.development
- functions/.env
- functions/.env.local
- functions/.secret.local
- other repo-documented local config files

Never print their secret values back into chat.

## Required Output

Return these sections in order:
1. Active mode
2. Repo status
3. Local-only status
4. Runtime blocker status
5. Recommended next action

## Required Behavior

### In Repo Alignment Mode
- confirm whether the current branch matches the tracked remote
- say whether the repo is clean or dirty
- separate tracked modifications from untracked local files
- identify local-only items without treating them as GitHub state
- do not ask for PATs, app secrets, or dashboard values

### In Runtime Integration Mode
- inspect local runtime files first
- only ask for missing values if a specific runtime task is blocked
- name the blocked workflow directly

## Forbidden Behavior
- asking for a GitHub PAT during repo alignment
- asking for app secrets before checking local files
- treating GitHub sync as equivalent to local runtime restoration
- claiming repo alignment without checking branch and remote
- claiming a secret is missing without checking the documented local paths

## Success Condition
The user should know:
- whether the repo is aligned
- what local-only state exists
- whether runtime setup is actually needed
- the one next step to take
