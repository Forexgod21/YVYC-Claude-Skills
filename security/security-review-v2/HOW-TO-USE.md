# Security Review v2 — How To Use

**Skill:** `security-review-v2`
**Category:** Security
**Author:** YourVisionYourCreation LLC
**Version:** 2.0
**License:** CC BY 4.0

---

## What This Skill Does

Security Review runs structured, red-team style security analysis that is
grounded in inspected artifacts — never in vibes. Every finding ships with an
exploit path, an impact, a fix mapped to a concrete enforcement layer, and the
verification required to prove the fix. Concerns without evidence are labeled
`Verification gap`, not promoted to vulnerabilities.

This is the first skill in the `security/` category — the doctrine layer for
GEAR UP Phase 2 and all future YVYC security work.

---

## The Problem It Solves

Most AI security reviews fail in one of two ways:

1. **Vague commentary** — "make sure you validate inputs" with no exploit
   path, no location, no fix
2. **Invented certainty** — assumptions presented as confirmed
   vulnerabilities, or conclusions delivered without inspecting anything

This skill bans both. Findings are evidence-first or they are labeled as gaps.

---

## When It Activates

Ask for any of these:

```
Run a security review on this.
```
```
Red team pass — what's exploitable here?
```
```
Threat model this feature before I build it.
```
```
Is this release security-ready?
```

It also self-activates when a task touches auth, roles, secrets, OAuth,
payments, external integrations, file/storage access, background execution,
or AI prompt/tool boundaries.

---

## The Finding Format

Every finding includes all five:

1. **Finding** — what is wrong
2. **Exploit path** — how an attacker actually reaches it
3. **Impact** — what it costs you
4. **Fix** — mapped to client / bridge / backend / rules / storage /
   monitoring / config
5. **Verification required** — the test that proves the fix

---

## Severity Language

No vague "medium/high" ranking unless you ask for it. Instead:

- `confirmed finding` — evidence-backed
- `verification gap` — plausible, not yet proven
- `design risk` — structural concern
- `blocked from inspection` — couldn't be checked from this surface

---

## The Three Review Modes

| Mode | When | Behavior |
|---|---|---|
| **Code review** | Code is available | Inspects code paths, cites files and functions |
| **Design review** | Only docs/architecture available | Maps trust boundaries and assumptions, marks unverified claims |
| **Runtime review** | Live or emulator behavior in scope | Separates observed behavior from inferred behavior |

---

## What You'll See

For substantial reviews, output in this order:

1. Confirmed findings
2. Verification gaps
3. Recommended fixes
4. Required tests
5. Evidence

---

## Installation

1. Copy the `SKILL.md` file from this folder
2. Place it in your Claude skills directory
3. Install `shared-kernel` (from `agentic/`) alongside it
4. It activates automatically on security-touching tasks, or on any explicit
   review request

---

*Part of the YVYC Claude Skills Library — Security Category*
*YourVisionYourCreation LLC — [yourvisionyourcreation.com](https://www.yourvisionyourcreation.com)*
*Licensed under CC BY 4.0 — Free to use with attribution to YourVisionYourCreation LLC*
