# Chat Strategy Guide v2 — How To Use

**Skill:** `chat-strategy-guide-v2`
**Category:** Agentic
**Author:** YourVisionYourCreation LLC
**Version:** 2.0
**License:** CC BY 4.0

---

## What This Skill Does

Chat Strategy Guide makes the Chat surface strong at what it is actually good
at — reasoning, planning, explanation, doctrine, and decision support — without
pretending it has powers it doesn't have. Chat cannot inspect your repo, run
your tests, or validate your runtime. This skill makes Claude say so plainly
and still deliver maximum strategic value from where it sits.

**Surface lock:** Chat only. In CoWork or Code, it stands down unless you
explicitly ask for an adaptation.

---

## The Problem It Solves

Chat sessions fail in two opposite directions:

1. **Pretending** — implying repo inspection, test runs, or build results that
   never happened, because the surface can't do them
2. **Collapsing** — retreating into generic advice when the task deserved
   original, high-level strategic thinking

This skill closes both failure modes: honest about capability, elite in
reasoning.

---

## The Four Chat Modes

| Mode | Triggers | What You Get |
|---|---|---|
| **Explanation** | "what does this mean", "why is this happening" | Plain language first, technical depth second |
| **Strategy** | "what should I do", "how should I structure this" | One clear direction with rationale — no option sprawl |
| **Planning** | "build plan", "rollout order", "implementation sequence" | Phases, blockers, dependencies — repo work separated from runtime work |
| **Learning** | Concept and terminology questions | Who/what/when/where/why with direct examples, no jargon walls |

---

## The Surface Handoff Rule

When a task belongs on another surface, Claude says which one and why —
without pretending the work already happened there:

- **CoWork** → repo state, local files, runtime blockers
- **Code** → code edits, test verification, implementation review
- **Chat** → strategy, doctrine, synthesis, explanation

---

## Example Prompts

```
Help me think through the architecture before I open Code. Strategy mode.
```
```
Explain what this error means — beginner terms first, then the technical version.
```
```
Give me the build plan: phases, blockers, and what belongs in CoWork vs Code.
```

---

## What You'll See

For substantial tasks:

1. Situation summary
2. Direct recommendation
3. Why that recommendation is correct
4. Which surface to use next (stay in Chat / move to CoWork / move to Code)

Smaller questions get direct answers without forced structure.

---

## Installation

1. Copy the `SKILL.md` file from this folder
2. Place it in your Claude skills directory
3. Install `shared-kernel` alongside it
4. It activates automatically on reasoning, planning, and teaching tasks in Chat

---

*Part of the YVYC Claude Skills Library — Agentic Category*
*YourVisionYourCreation LLC — [yourvisionyourcreation.com](https://www.yourvisionyourcreation.com)*
*Licensed under CC BY 4.0 — Free to use with attribution to YourVisionYourCreation LLC*
