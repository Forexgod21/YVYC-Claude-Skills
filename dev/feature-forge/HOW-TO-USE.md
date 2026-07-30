# Feature Forge — How To Use

**Skill:** `feature-forge`
**Category:** Dev
**Author:** YourVisionYourCreation LLC
**License:** CC BY 4.0

---

## What This Skill Does

Feature Forge turns a blank-page product idea into a real design: the
job-to-be-done in one sentence, the three hardest constraints named up
front, data model before API, API contract before implementation, failure
modes with blast radius, and a three-phase delivery plan with exit
criteria. It ships with a one-page design doc template and a build-vs-buy
framework.

The core principle: **design is decisions** — a design doc that only
describes what you chose, without the alternatives you rejected and why,
is incomplete.

---

## The Problem It Solves

Greenfield design fails the same few ways every time: designing against a
fuzzy target, drawing architecture before naming constraints, writing the
API before the data model, deferring error handling to a v2 that never
comes, and copying FAANG architecture for a 100-user product. This skill
walks the sequence in the only order that works and refuses the shortcuts
by name.

---

## Quick Start

```
Design a feature for member onboarding — architecture, data model, API,
and rollout plan.
```
```
How should I build a notification system for this app? Two engineers,
$50/month budget, 10k users.
```
```
Build vs buy: payments infrastructure for a marketplace at our scale.
```
```
Here's my idea — pressure it. What are the constraints and failure
modes I'm not seeing?
```

---

## The Design Sequence

| Step | Discipline |
|---|---|
| 1. Job-to-be-done | One sentence, user's voice — fuzzy target means stop and ask |
| 2. Constraints | Name the three hardest; they decide the architecture |
| 3. Data model | Entities, relationships, lifecycle, and the queries — before any API |
| 4. API contract | The contract is the test surface; it exists before implementation |
| 5. Failure modes | Every integration point gets timeout/error/blast-radius answers |
| 6. Phased delivery | Walking skeleton → MVP → production-hardened, each with exit criteria |

---

## What You Get Per Design

- A one-page design doc with goals, **non-goals**, constraints, rejected
  alternatives with reasons, a failure-mode table, a rollout plan, and a
  kill switch
- A scale point set at 10× current load — not 1× (rebuild in six months),
  not 100× (complexity tax you don't need yet)
- A build-vs-buy call with the reasoning stated

---

## What This Skill Will Refuse

- Designing against a fuzzy job statement
- "We'll figure out scale later" / "we'll add observability after launch"
  / "we'll handle errors in v2"
- Trendy tech chosen because it's cool — boring tech is an asset
- A feature with no rollback path, no kill switch, or no named owner

---

## Installation

1. Copy the `SKILL.md` file from this folder
2. Place it in your Claude skills directory
3. Install `shared-kernel` (from `agentic/`) alongside it — this skill
   loads it first
4. It activates automatically on any from-scratch design or architecture
   request

---

*Part of the YVYC Claude Skills Library — Dev Category*
*YourVisionYourCreation LLC — [yourvisionyourcreation.com](https://www.yourvisionyourcreation.com)*
*Licensed under CC BY 4.0 — Free to use with attribution to YourVisionYourCreation LLC*
