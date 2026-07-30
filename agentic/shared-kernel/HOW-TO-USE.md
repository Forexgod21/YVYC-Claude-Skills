# Shared Kernel — How To Use

**Skill:** `shared-kernel`
**Category:** Agentic
**Author:** YourVisionYourCreation LLC
**Version:** 2.0
**License:** CC BY 4.0

---

## What This Skill Does

Shared Kernel is the common spine of the YVYC skill federation — the
universal engineering discipline that loads before any specialist skill.
It enforces the posture that applies regardless of language, framework, or
platform: evidence before assumption, zero-defect output, scope
discipline, absolute security boundaries, verification gates before any
"done," and a no-filler output contract.

Every specialist skill in the library that opens with **"Load Order: Read
`shared-kernel/SKILL.md` first"** is invoking this file. The specialist
adds domain depth; it never overrides the kernel.

---

## The Problem It Solves

Without a kernel, every specialist skill has to re-teach the basics — and
drift creeps in between them:

- Claims about files nobody actually read
- APIs recommended for framework versions nobody verified
- TODOs and stubs shipped as finished work
- "While we're here" refactors that were never authorized
- "Done" declared with nothing compiled, run, or tested
- Security workarounds that disable the control instead of fixing the
  problem

The kernel closes all of it once, in one place, for every skill built on
top.

---

## Who Inherits It

Two federations run on this kernel:

- **The surface-doctrine suite** (`doctrine-guardian-v2`,
  `chat-strategy-guide-v2`, `code-verification-guard-v2`,
  `cowork-repo-bootstrap-v2`, `cowork-runtime-gatekeeper-v2`) — each of
  these also embeds its surface-specific kernel rules inline
- **The dev federation** (`angular-architect`, `debugging-wizard`,
  `devops-sre`, `discord-platform-expert`, `embedded-systems`,
  `feature-forge`, `security-reviewer`, and future specialists) — each
  opens with the Load Order line pointing here

---

## The Core Posture

| Pillar | The Rule |
|---|---|
| Evidence | Read the file, verify the version, quote the line — or say what's uncertain |
| Zero-defect | No TODOs, no stubs, no fragments; a patch that fails twice becomes a full rewrite |
| Scope | One primary recommendation; no unauthorized side-quests or surprise dependencies |
| Security | No secrets in output, no deploys without authorization, no disabled controls |
| Verification | Compiles/runs clean, tested against concrete input, rollback stated |
| Output | No preamble, no postamble — the work, in the project's own style |

---

## Installation

1. Copy the `SKILL.md` file from this folder
2. Place it in your Claude skills directory
3. Install any specialist skills on top — their Load Order lines resolve
   to this kernel
4. It activates automatically whenever a specialist loads or
   production-grade discipline is required

---

*Part of the YVYC Claude Skills Library — Agentic Category*
*YourVisionYourCreation LLC — [yourvisionyourcreation.com](https://www.yourvisionyourcreation.com)*
*Licensed under CC BY 4.0 — Free to use with attribution to YourVisionYourCreation LLC*
