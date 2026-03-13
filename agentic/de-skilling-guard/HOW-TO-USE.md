# How To Use: De-Skilling Guard

**Category:** Agentic
**Tier:** 3 — Ecosystem Level
**Skill File:** `SKILL.md`
**Source:** YVYC Agentic Skill Library — built on human-AI teaming research and
capability preservation frameworks.

---

## What This Skill Does

Turns Claude into a human-AI capability strategist that identifies, measures, and
prevents the erosion of human skills caused by over-reliance on AI agents. The
most underexamined risk in AI deployment isn't that AI will make a mistake — it's
that humans will gradually lose the ability to catch one. This skill addresses
that directly: it audits your AI workflows for de-skilling risk, checks whether
your human oversight is genuine or just the appearance of oversight, and designs
protocols to keep humans genuinely capable alongside their AI tools.

---

## When To Use It

- You're deploying AI tools and want to build skill preservation in from the start
- Your team has been using AI for a while and you're not sure if they're still sharp
- Your AI went down and humans struggled to cover — that's a red flag worth auditing
- You want to make sure your human reviewers can actually catch AI errors
- You're designing an AI-assisted workflow and want humans to stay genuinely capable

---

## How To Activate It

Once installed, activate this skill by saying something like:

> "Audit my AI workflow for de-skilling risk. Here's how it's structured: [description]"

Other ways to trigger it:
- "My team relies on AI for [task] — are they losing the skill to do it themselves?"
- "Design a capability preservation protocol for my AI-assisted team"
- "Check whether my human oversight is genuine or just theater"
- "How do I keep humans skilled when AI handles most of the work?"

---

## What To Provide

| Input | Required? | Example |
|---|---|---|
| Workflow description | Yes | "AI drafts all client reports, human reviews and approves" |
| Human roles affected | Yes | "3 analysts who used to write reports now only review AI drafts" |
| Current oversight structure | Yes | "Analysts read AI output, make edits, and approve for sending" |
| Time since AI adoption | No | "8 months" |
| Observed capability changes | No | "One analyst mentioned they'd struggle to write a report from scratch now" |

---

## Example Usage

**You say:**
> "Audit my workflow for de-skilling risk. We adopted an AI report writing tool
> 8 months ago. Three analysts who used to write all client reports now only
> review and approve AI drafts. They spend about 15 minutes per report vs. the
> 3 hours it used to take. Current oversight: they read the draft, make minor
> edits, and approve. One analyst mentioned last week she'd struggle to write a
> report from scratch now. We haven't had any AI errors get through to clients
> yet."

**Claude delivers:**
> A complete de-skilling assessment identifying report writing as High severity
> (meaningful degradation after 8 months), an oversight validity check flagging
> that 15-minute reviews of complex reports likely cannot catch sophisticated
> analytical errors, and a capability preservation protocol including quarterly
> unassisted report writing exercises, monthly blind evaluation sessions, and a
> workflow redesign recommendation that assigns novel or high-stakes reports to
> human-first drafting to maintain active skill development.

---

## The Critical Distinction This Skill Makes

**Oversight Theater vs. Real Oversight**

A human who reviews AI output but can no longer independently evaluate its quality
is not providing oversight. They are providing the *appearance* of oversight. This
is the most dangerous de-skilling outcome because it creates the feeling of safety
without the substance of it.

This skill specifically checks for this — and flags it when it finds it.

---

## Pro Tips

- The analyst who said "I'd struggle to write a report from scratch" is telling
  you exactly what the audit will find — trust those observations
- De-skilling accelerates invisibly. Humans rarely notice until they're under
  pressure and the skill isn't there
- Preservation protocols only work if they're scheduled and enforced — vague
  intentions to "stay sharp" don't hold against daily productivity pressure
- The goal isn't to make AI less useful — it's to make sure humans stay capable
  enough to govern AI effectively
- Rerun this audit every 6 months for any workflow where AI handles high-stakes tasks

---

## How This Fits The YVYC Agentic Stack

| Skill | Role in Stack |
|---|---|
| `de-skilling-guard` | Preserves human capability alongside AI delegation (this skill) |
| `human-in-loop-escalation` | Ensures oversight roles are staffed by genuinely capable humans |
| `trust-calibration` | Prevents over-trust that leads to under-scrutiny |
| `monitoring-protocol` | Detects behavioral signals of capability erosion in oversight |
| `zone-of-indifference-override` | Keeps humans engaged on decisions that matter |
| `cognitive-friction` | Maintains deliberate human thinking at key decision points |

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
