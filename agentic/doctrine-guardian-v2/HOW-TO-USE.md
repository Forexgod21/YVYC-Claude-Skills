# Doctrine Guardian v2 — How To Use

**Skill:** `doctrine-guardian-v2`
**Category:** Agentic
**Author:** YourVisionYourCreation LLC
**Version:** 2.0
**License:** CC BY 4.0

---

## What This Skill Does

Doctrine Guardian is the operating doctrine layer for Anthropic surfaces. It
enforces scope discipline, evidence-first reasoning, surface awareness, and
approval boundaries before Claude performs analysis, implementation, runtime
setup, or release actions.

It works across all three surfaces:

| Surface | What It Governs |
|---|---|
| Chat | Reasoning, planning, explanation, policy |
| CoWork | Workspace inspection, repo alignment, runtime gating |
| Code | Code changes, verification, implementation discipline |

---

## The Problem It Solves

The most expensive AI failures are not wrong answers — they are silent
escalations and false confidence:

- A planning request quietly becomes an execution run
- A repo-alignment request quietly becomes runtime setup
- A code change quietly becomes a deployment path
- "It should work" gets presented as "it was verified"
- Local machine state gets treated as GitHub state

Doctrine Guardian makes every one of those transitions explicit and puts them
behind user approval.

---

## When It Activates

- The task touches implementation, analysis, review, security, auth, secrets,
  billing, OAuth, deployment, hosting, or public exposure
- The user asks for readiness, signoff, review, or judgment
- The request is ambiguous and drift risk is present
- Claude is about to move from one working mode into another

---

## The Approval Boundaries

Claude must not cross these lines without explicit user intent:

- repo work → runtime setup
- runtime setup → deployment
- local debugging → external dashboard changes
- planning → destructive action
- analysis → conclusion without inspection

---

## What You'll See

For non-trivial tasks, output includes five blocks:

1. **Active mode**
2. **Scope**
3. **Assumptions**
4. **Recommendation**
5. **Verification or evidence status**

Non-trivial conclusions come with an evidence block:

```
### Evidence
- Inspected:
- Actions:
- Observed:
- Conclusion mapping:
```

If nothing was inspected, the block says `Not inspected yet` — never a bluff.

---

## Example Prompts

```
Run this under doctrine. What mode are we in and what's in scope?
```
```
Before you touch anything — scope this task and tell me what you'd need to inspect.
```
```
Is this ready to ship? Evidence-first answer only.
```

---

## Installation

1. Copy the `SKILL.md` file from this folder
2. Place it in your Claude skills directory
3. Install `shared-kernel` alongside it (the kernel it enforces)
4. It activates automatically on qualifying tasks — no invocation phrase needed

---

*Part of the YVYC Claude Skills Library — Agentic Category*
*YourVisionYourCreation LLC — [yourvisionyourcreation.com](https://www.yourvisionyourcreation.com)*
*Licensed under CC BY 4.0 — Free to use with attribution to YourVisionYourCreation LLC*
