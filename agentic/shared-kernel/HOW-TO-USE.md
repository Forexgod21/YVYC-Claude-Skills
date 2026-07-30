# Shared Kernel — How To Use

**Skill:** `shared-kernel`
**Category:** Agentic
**Author:** YourVisionYourCreation LLC
**Version:** 1.0
**License:** CC BY 4.0

---

## What This Skill Does

Shared Kernel is the foundation layer of the YVYC Surface Doctrine suite. It
defines the rules every other doctrine skill inherits: surface awareness,
evidence discipline, scope discipline, and secret handling.

It teaches Claude three things that default behavior gets wrong:

1. **Anthropic surfaces are not interchangeable.** Chat, CoWork, and Code have
   different tools and different powers. A claim that requires repo inspection
   cannot be made from a surface that has no repo access.
2. **Evidence comes before conclusions.** If inspection did not happen, the
   answer is `Not inspected yet` — not a confident guess.
3. **Secrets are requested last, not first.** Local files get checked before
   the user is ever asked to paste a value.

---

## The Problem It Solves

Without a kernel, AI sessions drift:

- Claude implies it inspected files it never opened
- Claude asks for PATs and app secrets it doesn't need
- Repo alignment work silently escalates into runtime setup
- Local machine state gets confused with GitHub state
- Conclusions get delivered with confidence that evidence doesn't support

Shared Kernel stops all of it at the root, so every skill built on top of it
starts from the same discipline.

---

## The Two Working Modes

| Mode | Use For | Hard Rule |
|---|---|---|
| **Repo Alignment Mode** | Opening a repo, checking branches, comparing local to remote, resuming work | Inspect git state and local files first. Never ask for secrets. |
| **Runtime Integration Mode** | Emulator testing, OAuth flows, broker testing, external service setup | Only enters on explicit user request. Check local env/secret paths before asking for anything. |

One mode at a time. The active mode is always named.

---

## How To Use It

Shared Kernel is a dependency, not a standalone workflow. Install it alongside
the skills that inherit it:

- `doctrine-guardian-v2` — the cross-surface doctrine layer
- `chat-strategy-guide-v2` — Chat surface
- `code-verification-guard-v2` — Code surface
- `cowork-repo-bootstrap-v2` — CoWork session start
- `cowork-runtime-gatekeeper-v2` — CoWork runtime gating

Once installed, it activates automatically whenever surface, evidence, or
scope discipline is in play. No trigger phrase required.

---

## What You'll See

- Claude names which mode is active before non-trivial work
- `Not inspected yet` appears instead of invented certainty
- Evidence blocks list what was inspected, what was done, what was observed
- Secret requests only happen after local paths were checked — and never echo
  values back into chat

---

## Installation

1. Copy the `SKILL.md` file from this folder
2. Place it in your Claude skills directory
3. Install the doctrine skills that inherit it (see list above)
4. It activates automatically — no invocation phrase needed

---

*Part of the YVYC Claude Skills Library — Agentic Category*
*YourVisionYourCreation LLC — [yourvisionyourcreation.com](https://www.yourvisionyourcreation.com)*
*Licensed under CC BY 4.0 — Free to use with attribution to YourVisionYourCreation LLC*
