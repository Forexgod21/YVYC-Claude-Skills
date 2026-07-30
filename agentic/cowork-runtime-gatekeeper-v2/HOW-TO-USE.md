# CoWork Runtime Gatekeeper v2 — How To Use

**Skill:** `cowork-runtime-gatekeeper-v2`
**Category:** Agentic
**Author:** YourVisionYourCreation LLC
**Version:** 2.0
**License:** CC BY 4.0

---

## What This Skill Does

CoWork Runtime Gatekeeper controls the single most abused transition in
AI-assisted development: the jump from repo work into runtime work. No
emulator setup, OAuth flow, broker testing, or external integration begins
without explicit user authorization — and no secret is ever requested before
the local files that might already contain it have been checked.

**Surface lock:** CoWork only. In Chat or Code, it stands down unless you
explicitly ask for an adaptation.

---

## The Problem It Solves

- `.env` and PAT requests for tasks that never needed them
- Hidden jumps into OAuth, broker, emulator, or dashboard setup mid-task
- Being asked to paste a secret that already exists in
  `functions/.secret.local`
- Code work and environment work blurred into one confused session

---

## The Decision Rule

Before any secret or runtime config is requested, exactly one case must be
true:

| Case | Condition | Behavior |
|---|---|---|
| **1 — Repo work only** | Code review, repo sync, branch inspection, planning, documentation | Stay in Repo Alignment Mode. No secrets. No dashboard values. |
| **2 — Runtime work requested** | You explicitly asked to run an emulator, broker, OAuth, or end-to-end flow | Switch to Runtime Integration Mode — inspect local paths first. |

---

## The Secret Request Rule

A secret may only be requested when **all three** are true:

1. You explicitly want runtime integration or runtime testing
2. The relevant local file path was inspected
3. The required key is actually missing

Any condition false → no request. And if a local file already holds the
value, Claude uses the file — it never asks you to paste the value into chat.

---

## When Blocked, You Get Exactly This

1. Active mode
2. Blocked workflow
3. Inspected paths
4. Missing file
5. Missing key names
6. Why that runtime task needs them
7. One next action

---

## Example Prompts

```
Continue working on the repo. (→ no secrets should ever come up)
```
```
Now I want to test the OAuth flow end to end. (→ runtime mode, local paths checked first)
```
```
Why are you asking me for that key? Which path did you check?
```

---

## Installation

1. Copy the `SKILL.md` file from this folder
2. Place it in your Claude skills directory
3. Install `shared-kernel` alongside it, and pair with
   `cowork-repo-bootstrap-v2` for full CoWork discipline
4. It activates automatically whenever the conversation touches secrets,
   tokens, OAuth, emulators, or runtime testing

---

*Part of the YVYC Claude Skills Library — Agentic Category*
*YourVisionYourCreation LLC — [yourvisionyourcreation.com](https://www.yourvisionyourcreation.com)*
*Licensed under CC BY 4.0 — Free to use with attribution to YourVisionYourCreation LLC*
