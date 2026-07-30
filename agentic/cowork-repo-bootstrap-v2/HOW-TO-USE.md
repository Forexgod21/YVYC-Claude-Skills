# CoWork Repo Bootstrap v2 — How To Use

**Skill:** `cowork-repo-bootstrap-v2`
**Category:** Agentic
**Author:** YourVisionYourCreation LLC
**Version:** 2.0
**License:** CC BY 4.0

---

## What This Skill Does

CoWork Repo Bootstrap makes every CoWork session start with inspection, not
interrogation. Before Claude asks you for anything — a branch name, a token, a
config value — it establishes the actual state of the repo and the local
machine itself.

**Surface lock:** CoWork only. In Chat or Code, it stands down unless you
explicitly ask for an adaptation.

---

## The Problem It Solves

- Sessions that open with "can you paste your PAT?" when the repo is already
  cloned locally
- False assumptions about which branch you're on
- Local machine state confused with GitHub state
- "What's missing?" answered by guessing instead of by looking

---

## When It Activates

- A repository is opened
- "Continue working" / "get me up to speed"
- "Clone this repo here"
- "What's missing locally versus GitHub?"
- You switch machines and want continuity

---

## The Inspection Order

1. Workspace root contents
2. Repo instructions if present
3. Current git branch
4. Current commit
5. Remote configuration
6. Ahead/behind status versus tracked remote
7. Local modified tracked files
8. Local untracked files
9. Nested repos
10. Standard local env and secret paths (`.env`, `.env.local`,
    `functions/.secret.local`, etc.)
11. Runtime blockers — only if runtime mode was explicitly requested

Secret values are never printed back into chat. Only file presence is
reported.

---

## What You'll See

Every bootstrap returns five sections in order:

1. **Active mode**
2. **Repo status** — branch, remote alignment, clean or dirty
3. **Local-only status** — untracked files and local state, clearly separated
   from GitHub state
4. **Runtime blocker status**
5. **Recommended next action** — one step, not a menu

---

## Example Prompts

```
Get me up to speed on this repo.
```
```
I just switched machines — where did we leave off, and what's local-only here?
```
```
Compare my local state to GitHub before we do anything.
```

---

## Installation

1. Copy the `SKILL.md` file from this folder
2. Place it in your Claude skills directory
3. Install `shared-kernel` alongside it, and pair with
   `cowork-runtime-gatekeeper-v2` for full CoWork discipline
4. It activates automatically when a repo opens in CoWork

---

*Part of the YVYC Claude Skills Library — Agentic Category*
*YourVisionYourCreation LLC — [yourvisionyourcreation.com](https://www.yourvisionyourcreation.com)*
*Licensed under CC BY 4.0 — Free to use with attribution to YourVisionYourCreation LLC*
