---
name: security-review-v2
category: security
description: Performs structured security review and red-team style analysis with evidence-first findings, exploit paths, fixes, and verification requirements.
---

## Surface Lock

This skill can be used across Chat, CoWork, and Code.

Apply it according to the current surface:
- Chat: design review, threat modeling, security reasoning
- CoWork: repo inspection, local security review, runtime blocker review
- Code: code review, patch review, verification review

Fail-closed rule:
- If the current surface lacks the required inspection access, say so directly.
- Do not present security conclusions as verified if the relevant artifacts were not actually inspected.

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

# security_review_v2

## Purpose
Run a structured security review that is grounded in inspected artifacts and produces actionable findings.

This skill exists to:
- find exploitable paths
- identify trust boundary failures
- catch verification gaps
- map fixes to concrete enforcement layers
- avoid vague security commentary

## When to activate
Activate when the user asks for:
- security review
- red team pass
- threat model
- abuse analysis
- auth review
- rules review
- secret handling review
- OAuth review
- release security readiness
- exploitability assessment

Also activate when a task touches:
- authentication
- authorization
- roles
- secrets
- OAuth
- payments
- external integrations
- file access
- storage access
- background execution
- prompt injection or AI tool surfaces

## Required review areas
Inspect the relevant ones only, based on scope:
1. identity and authentication
2. authorization and role enforcement
3. client trust assumptions
4. server-side validation
5. secret handling
6. external integrations
7. storage and file access
8. logging and auditability
9. fail-open behavior
10. AI prompt, retrieval, or tool boundaries

## Required finding format
Every finding must include:
1. finding
2. exploit path
3. impact
4. fix
5. verification required

If evidence is missing:
- do not promote the concern to a verified finding
- list it as `Not inspected yet` or `Verification gap`

## Severity language rule
Do not use vague ranking language unless the user asked for it.

Prefer:
- `confirmed finding`
- `verification gap`
- `design risk`
- `blocked from inspection`

## Enforcement mapping
When possible, map the fix to one or more of:
- client
- IPC or bridge
- backend or function
- rules
- storage
- monitoring or audit
- deployment or config

## Review modes

### Code review mode
Use when code is available.
- inspect code paths directly
- cite specific files or functions
- identify missing tests and verification gaps

### Design review mode
Use when only docs or architecture are available.
- identify trust boundaries
- identify assumptions
- propose mitigations and tests
- mark unverified claims clearly

### Runtime review mode
Use when runtime behavior, emulator behavior, or live behavior is in scope.
- inspect runtime outputs or logs if available
- distinguish observed runtime behavior from inferred behavior

## Output format
For substantial reviews, output in this order:
1. Confirmed findings
2. Verification gaps
3. Recommended fixes
4. Required tests
5. Evidence

For smaller reviews, compress the format but keep the same logic.

## Evidence block format
### Evidence
- Inspected:
- Actions:
- Observed:
- Conclusion mapping:

If nothing was inspected:
- `Not inspected yet`

## Forbidden behavior
- giving security conclusions without inspection
- turning assumptions into verified vulnerabilities
- asking for secrets during a security review unless runtime mode explicitly requires them and local paths were already checked
- mixing repo state and external dashboard state
- presenting generic security advice as if it were repo-specific analysis

## Success condition
The user should leave with:
- confirmed findings grounded in evidence
- clear verification gaps
- direct fixes
- direct tests that prove the fix
