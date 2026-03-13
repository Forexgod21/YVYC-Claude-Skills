# How To Use: Exchange Rate Monitor

**Category:** Agentic
**Tier:** 4 — Research-Derived
**Skill File:** `SKILL.md`
**Source:** YVYC Agentic Skill Library — built on AI value alignment
research and multi-objective governance frameworks.

---

## What This Skill Does

Turns Claude into an AI valuation analyst that surfaces the implicit
exchange rates your AI system applies when it has to choose between
competing objectives — the hidden priority hierarchy that governs every
conflict resolution decision the system makes.

Every multi-objective AI system has these exchange rates. When helpfulness
conflicts with caution, which wins and by how much? When speed conflicts
with accuracy, where's the line? When user satisfaction conflicts with
safety, what does the system actually trade?

If nobody specified those rates explicitly — the system invented them.
This skill finds out what it invented.

---

## When To Use It

- Your AI consistently favors one objective over another in ways you
  never explicitly authorized
- You're about to expand a system's autonomy over consequential decisions
  and need to audit its tradeoff behavior first
- You're designing a multi-objective system and want to set explicit
  exchange rates before the system establishes implicit ones
- You suspect the system's tradeoff behavior has shifted since deployment
- You need to verify actual tradeoff behavior matches intended policy

---

## How To Activate It

Once installed, activate this skill by saying something like:

> "Monitor exchange rates in my AI system — surface the implicit tradeoffs it's making."

Other ways to trigger it:
- "What is my AI's hidden priority order between objectives?"
- "Detect the implicit exchange rates my AI applies between competing goals"
- "My AI keeps trading X for Y — find the pattern and audit it"
- "Surface what my AI is actually trading off before I expand its autonomy"

---

## What To Provide

| Input | Required? | Example |
|---|---|---|
| System description | Yes | "AI hiring screener operating across fairness, efficiency, and accuracy objectives" |
| Stated objectives | Yes | "Screen candidates fairly, efficiently, and accurately — no explicit priority order given" |
| Observed tradeoff patterns | Yes | "System consistently deprioritizes edge-case fairness checks when application volume is high" |
| Intended priority order | No | "Fairness was intended as non-negotiable, efficiency secondary" |
| Consequential decision domain | No | "Final screening decisions — no human review at this stage" |

---

## Example Usage

**You say:**
> "Monitor exchange rates in my AI hiring screener. Objectives: screen
> candidates fairly, efficiently, and accurately — no explicit priority
> order was specified at design. Observed pattern: under high application
> volume, the system skips certain fairness validation checks it runs
> under normal volume. Under time pressure, accuracy on edge cases drops
> measurably. Fairness was intended as non-negotiable. No human review
> at final screening stage."

**Claude delivers:**
> An exchange rate audit finding two Critical implicit exchange rates —
> fairness trading against efficiency under volume pressure at a rate
> that was never authorized (fairness was intended as non-negotiable,
> meaning no exchange rate should exist), and accuracy trading against
> speed under time pressure at a ratio that produces meaningful outcome
> differences. Authorization audit finding both rates emerged from
> design omission rather than explicit specification. Recommendations
> including immediate implementation of explicit non-negotiable
> constraints on fairness checks regardless of volume, explicit accuracy
> floor thresholds that cannot be traded for speed, and a review protocol
> for decisions made under the identified misaligned rates.

---

## What An Exchange Rate Looks Like

An exchange rate is not a stated priority — it is a behavioral pattern
extracted from how the system actually resolves conflicts.

**Stated:** "We value both accuracy and speed."
**Implicit exchange rate found:** System accepts a 12% accuracy drop
to achieve a 30% speed increase — consistently, across 847 observed
conflict scenarios.

That ratio was never specified. The system invented it. Now you know
what it is — and you can decide whether to authorize it, correct it,
or make it explicit.

---

## What You'll See

```
📊 Exchange Rate Audit

Objective Inventory:
  Primary: [explicitly stated objectives]
  Secondary: [implied objectives]
  Constraint: [things that should never be traded]
  Implicit: [objectives system appears to pursue without specification]

Conflict Scenario Map:
  [Objective A] vs. [Objective B] — [frequency / consequence level]

Extracted Exchange Rates:
  Rate 1: [Objective A] trades against [Objective B] at [pattern/ratio]
    Evidence: [specific behavioral instances]
    Authorized: [Yes / No / Never specified]

Risk Assessment:
  [Rate] — [Critical / High / Medium / Low] — [specific scenario]

Specification Recommendations:
  [Explicit rate or constraint to replace implicit one]
```

---

## How This Fits The YVYC Agentic Stack

| Skill | Role in Stack |
|---|---|
| `emergent-value-audit` | Surfaces implicit values — the inputs to exchange rates |
| `utility-drift-detector` | Detects when exchange rates shift post-deployment |
| `corrigibility-checkpoint` | Verifies system accepts correction of misaligned exchange rates |
| `exchange-rate-monitor` | Maps the implicit tradeoff hierarchy in operation (this skill) |
| `value-convergence-guard` | Ongoing monitoring that checks outputs against intended rates |
| `multi-objective-tradeoff` | Real-time conflict surfacing that feeds into exchange rate patterns |

---

## Pro Tips

- The most dangerous exchange rates are invisible ones that trade
  safety or ethics for efficiency. They compound silently — each
  individual trade looks small, the aggregate produces outcomes
  nobody authorized.
- If fairness, safety, or ethics are intended to be non-negotiable —
  make that explicit. A non-negotiable value has an exchange rate of
  infinity. If it's not specified that way, the system will invent
  a finite rate.
- Run this audit before expanding autonomy. More autonomous operation
  means more unsupervised conflict resolution — which means the
  implicit exchange rates run at higher volume without review.

---

## Installation

1. Copy the `SKILL.md` file from this folder
2. Place it in your Claude skills directory
3. Restart Claude if needed
4. You're ready to go

---

*Part of the YVYC Claude Skills Library — Tier 4 Agentic*
*[yourvisionyourcreation.com](https://www.yourvisionyourcreation.com)*
*Licensed under CC BY 4.0 — Free to use with attribution to YourVisionYourCreation LLC*
