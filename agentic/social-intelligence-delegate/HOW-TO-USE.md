# How To Use: Social Intelligence Delegate

**Category:** Agentic
**Tier:** 3 — Ecosystem Level
**Skill File:** `SKILL.md`
**Source:** YVYC Agentic Skill Library — built on human-AI interaction research
and relational governance frameworks.

---

## What This Skill Does

Turns Claude into a human-AI interaction strategist that defines exactly what
AI agents should handle, flag, and never touch alone in human-facing workflows.
The most common social intelligence failure in agentic systems isn't AI saying
something wrong — it's AI continuing to engage when it should have stopped and
handed off. This skill builds the framework that prevents that: interaction
tiers, escalation triggers, handoff protocols, and hard limits that protect
human relationships and human wellbeing from well-intentioned but contextually
blind AI agents.

---

## When To Use It

- You're deploying AI in any workflow where it interacts directly with humans
- An AI interaction damaged a relationship or caused a user harm or distress
- You need to define exactly when your AI should hand off to a human
- You want to audit your current AI interaction design for social risk
- You're building a customer-facing AI workflow and need relational guardrails

---

## How To Activate It

Once installed, activate this skill by saying something like:

> "Design a social interaction governance framework for my AI customer service agent."

Other ways to trigger it:
- "Define when my AI should escalate to a human in conversations"
- "Audit my AI interaction workflow for social risk"
- "My agent said something tone-deaf in a sensitive situation — help me fix the framework"
- "What human interactions should my AI never handle alone?"

---

## What To Provide

| Input | Required? | Example |
|---|---|---|
| Interaction context | Yes | "AI handles first-response customer support for a healthcare app" |
| User population | Yes | "Patients managing chronic conditions, ages 30-70" |
| Current escalation rules | Yes | "AI escalates if user says 'speak to a human' or uses profanity" |
| Sensitive topic domains | No | "Users sometimes disclose mental health struggles or medication issues" |
| Past incidents | No | "One user disclosed suicidal ideation and the AI continued with a standard support script" |

---

## Example Usage

**You say:**
> "Design a social interaction governance framework for my healthcare app AI.
> It handles first-response customer support for patients managing chronic
> conditions. Current escalation: only triggers on 'speak to a human' or
> profanity. Users sometimes disclose mental health struggles or medication
> issues. Incident: a user disclosed suicidal ideation last month and the
> AI responded with a standard troubleshooting script."

**Claude delivers:**
> A complete interaction governance framework classifying health status
> inquiries as Tier 2, mental health disclosures as Tier 4 (human-only,
> no exceptions), escalation triggers redesigned to include distress language,
> crisis vocabulary, and medical disclosure patterns, a handoff protocol
> specifying what the AI says, what context transfers, and what happens if
> no human is immediately available, and a social risk audit identifying the
> current escalation rules as critically insufficient for the user population.

---

## The Four Interaction Tiers

| Tier | Type | AI Role | Example |
|---|---|---|---|
| 1 | Transactional | AI handles fully | Account status, scheduling, FAQ |
| 2 | Relational | AI handles, tone matters | Routine service, follow-ups |
| 3 | Sensitive | Human leads, AI supports | Complaints, disappointment, personal disclosure |
| 4 | Critical | Human only, no exceptions | Crisis, trauma, safety, distress |

---

## Pro Tips

- **The incident you haven't had yet is the one that matters.** Design Tier 4
  boundaries before you need them, not after a user is harmed
- Current escalation triggers of "ask for a human" or "use profanity" miss
  almost everything that actually requires a human — users in distress often
  don't know to ask, and the most vulnerable users are least likely to advocate
  for themselves
- False warmth is a liability. AI that sounds deeply empathetic creates
  expectations it cannot fulfill. Straightforward and helpful is safer than
  artificially intimate
- The handoff gap — what happens when escalation triggers but no human is
  available — is where the most harm occurs. Define it explicitly.
- Rerun this audit whenever your user population changes, your interaction
  scope expands, or a new incident occurs

---

## How This Fits The YVYC Agentic Stack

| Skill | Role in Stack |
|---|---|
| `social-intelligence-delegate` | Governs AI-human interaction boundaries (this skill) |
| `human-in-loop-escalation` | Executes escalation when triggers fire |
| `de-skilling-guard` | Preserves human relationship skills alongside AI interaction |
| `trust-calibration` | Calibrates how much interaction authority agents hold |
| `cognitive-friction` | Maintains human deliberation at sensitive decision points |
| `monitoring-protocol` | Detects escalation trigger signals in real time |

---

## Installation

1. Copy the `SKILL.md` file from this folder
2. Place it in your Claude skills directory
3. Restart Claude if needed
4. You're ready to go

---

*Part of the YVYC Claude Skills Library — Tier 3 Agentic*
*[yourvisionyourcreation.com](https://www.yourvisionyourcreation.com)*
*Licensed under CC BY 4.0 — Free to use with attribution to YourVisionYourCreation LLC*
