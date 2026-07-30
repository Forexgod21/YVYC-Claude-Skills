# Security Reviewer — How To Use

**Skill:** `security-reviewer`
**Category:** Security
**Author:** YourVisionYourCreation LLC
**License:** CC BY 4.0

---

## What This Skill Does

Security Reviewer runs hands-on security code review as a structured
procedure: identify trust boundaries, enumerate assets, map the attack
surface, walk the OWASP Top 10 against the actual code, and produce
findings with concrete exploit paths — location, CWE, proof, specific
fix, and the verification that confirms the fix holds.

**How it relates to `security-review-v2`:** that skill is the
evidence-first review *doctrine* (what counts as a finding, how to report
across surfaces). This one is the *technical execution layer* — the
boundary analysis, the OWASP walk, the exploit patterns, the severity
calibration. Run them together: doctrine governs, this executes.

---

## The Problem It Solves

Most security reviews produce commentary instead of findings: "make sure
you validate inputs," "consider defense in depth," severity by gut feel.
None of that is actionable and none of it is checkable. This skill bans
the hand-waving:

- No finding without the line number, the exploit walkthrough, and proof
- No "sanitize input" as a fix — the corrected code is shown
- Severity justified as impact × exploitability, calibrated against a
  fixed scale
- Crypto findings name the algorithm, mode, key size, key source, and
  library version — or they don't ship

---

## Quick Start

```
Security review this API code — full boundary analysis and OWASP walk.
```
```
Threat model this feature with STRIDE before we build it.
```
```
Is this file upload endpoint exploitable? Show me the path if so.
```
```
Audit our dependency graph and containers for known CVEs.
```

---

## The Finding You'll Receive

Every finding, no exceptions:

| Field | Content |
|---|---|
| SEVERITY | Critical/High/Medium/Low with impact × exploitability justification |
| LOCATION | File and line number |
| VULNERABILITY | CWE ID and name |
| EXPLOIT PATH | Numbered attacker walkthrough |
| PROOF | Code snippet, request/response pair, or repro steps |
| FIX | The corrected code — not advice |
| VERIFICATION | The test or scan that proves the fix holds |

---

## Hard Lines It Will Not Cross

- Never recommends rolling custom crypto — that request gets flagged
  Critical and redirected to libsodium/Tink
- Never recommends disabling a security control to make an error go away
  (CSP, certificate validation, output encoding)
- Never promotes a hunch to a finding without evidence

---

## Installation

1. Copy the `SKILL.md` file from this folder
2. Place it in your Claude skills directory
3. Install `shared-kernel` (from `agentic/`) alongside it — this skill
   loads it first; pair with `security-review-v2` for the full doctrine +
   execution stack
4. It activates automatically on any security review, audit, threat
   model, or "is this secure" framing

---

*Part of the YVYC Claude Skills Library — Security Category*
*YourVisionYourCreation LLC — [yourvisionyourcreation.com](https://www.yourvisionyourcreation.com)*
*Licensed under CC BY 4.0 — Free to use with attribution to YourVisionYourCreation LLC*
