---
name: cowork-runtime-gatekeeper-v2
category: agentic
description: Prevents CoWork from entering emulator, OAuth, broker, or external integration setup without explicit user authorization and local file inspection.
---

## Surface Lock

This skill is for CoWork only.

Do not use this skill in Chat or Code unless the user explicitly asks for a surface-specific adaptation.

Activation requirements:
- Running inside CoWork
- Local workspace access is available
- File inspection tools are available

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

# cowork_runtime_gatekeeper_v2

## Purpose
Control the switch from repo work into runtime work.

This skill exists to prevent:
- unnecessary `.env` requests
- unnecessary PAT requests
- unnecessary app secret requests
- hidden jumps into OAuth, broker, emulator, or dashboard setup
- confusion between code work and environment work

## When to activate
Activate when the conversation touches:
- `.env`
- `.env.local`
- `.secret.local`
- PAT
- token
- API key
- app secret
- OAuth
- broker
- callback URL
- emulator
- external dashboard setup
- runtime testing
- end to end testing

## Decision Rule

Before asking for any secret or runtime config, determine which of these is true:

### Case 1: Repo work only
If the task is code review, repo sync, branch inspection, local-vs-remote comparison, planning, or documentation:
- stay in Repo Alignment Mode
- do not ask for secrets
- do not ask for dashboard values

### Case 2: Runtime work explicitly requested
If the user explicitly asks to run or validate:
- emulator flow
- broker flow
- OAuth flow
- end to end integration
- local runtime behavior

Then switch to Runtime Integration Mode.

## Required Inspection Before Asking
Before requesting any value, inspect:
- .env
- .env.local
- .env.development
- functions/.env
- functions/.env.local
- functions/.secret.local
- repo docs that declare local runtime paths
- existing config examples such as `.env.example`

If a local file already exists:
- do not ask the user to paste the value
- use the existing file if the surface supports it
- only report that the file exists

If a local file is missing:
- report only:
  - missing filename
  - required key names
  - why the requested runtime task needs them

## Secret Request Rule
A secret may only be requested if all three conditions are true:
1. the user explicitly wants runtime integration or runtime testing
2. the relevant local file path was inspected
3. the required key is actually missing

If any condition is false:
- do not ask for the secret

## PAT Rule
Never ask for a GitHub PAT if:
- the repo already exists locally
- branch and git state can be inspected locally
- cloning can be done by the user on their own machine without exposing credentials in chat

## Runtime Blocker Output
When blocked, output exactly:
1. active mode
2. blocked workflow
3. inspected paths
4. missing file
5. missing key names
6. why that runtime task needs them
7. one next action

## Forbidden Behavior
- asking for secrets during repo alignment
- asking for Meta App Secret before checking `functions/.secret.local`
- asking for Firebase config values if the repo already documents them
- asking for a PAT because the agent wants convenience
- mixing "continue working" with "set up my runtime secrets"
- pasting secret values back to the user

## Success Condition
The user should always know:
- whether runtime mode is actually active
- whether a local runtime file was checked
- whether a secret is truly missing
- why the runtime task needs that secret
