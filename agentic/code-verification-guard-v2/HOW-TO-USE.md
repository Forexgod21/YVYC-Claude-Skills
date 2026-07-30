# Code Verification Guard v2 — How To Use

**Skill:** `code-verification-guard-v2`
**Category:** Agentic
**Author:** YourVisionYourCreation LLC
**Version:** 2.0
**License:** CC BY 4.0

---

## What This Skill Does

Code Verification Guard enforces implementation discipline on the Code
surface: read before writing, verify after changing, and never claim a test
passed that never ran. It also carries the Innovation Rule — Claude is
required to use strong modern patterns and allowed to create new components
when the task justifies them, but novelty without justification is not
innovation.

**Surface lock:** Code only. In Chat or CoWork, it stands down unless you
explicitly ask for an adaptation.

---

## The Problem It Solves

- Code changes shipped without re-reading the changed files
- "Tests pass" claimed when tests were never run
- Ripple effects (imports, references, types, stale docs) left behind
- Environment blockers misdiagnosed as code defects — and vice versa
- Weak legacy patterns copied forward because they already existed

---

## The Core Discipline

1. Read the relevant code before proposing concrete changes
2. Match the repo's actual patterns — or justify the stronger one
3. After editing, re-read changed files top to bottom
4. Check ripple effects: imports, references, types, tests, stale comments
5. Never claim verification that did not happen
6. Distinguish: code issue vs config issue vs secret issue vs runtime issue
   vs external service issue

---

## The Completion Rule

"Done" is only allowed when all four are true:

1. The requested code work is implemented
2. Relevant verification ran — or the missing verification was disclosed
3. No known requested work remains unaddressed
4. Stale references created by the change were cleaned up

---

## Review Mode

When you ask for a code review, output comes in this order:

1. **Findings** — what is wrong, where, why it matters, what should change
2. **Verification gaps** — what could not be checked
3. **Summary** — brief, last

No findings? It says so clearly, along with any remaining gaps.

---

## Example Prompts

```
Implement this, then give me: what changed, why, verification status, blockers.
```
```
Review this diff. Findings first, evidence second, summary last.
```
```
Is this change actually complete under the completion rule?
```

---

## Installation

1. Copy the `SKILL.md` file from this folder
2. Place it in your Claude skills directory
3. Install `shared-kernel` alongside it
4. It activates automatically on code edits, reviews, and debugging in Code

---

*Part of the YVYC Claude Skills Library — Agentic Category*
*YourVisionYourCreation LLC — [yourvisionyourcreation.com](https://www.yourvisionyourcreation.com)*
*Licensed under CC BY 4.0 — Free to use with attribution to YourVisionYourCreation LLC*
