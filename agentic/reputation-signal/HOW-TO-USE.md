# How To Use: Reputation Signal

**Category:** Agentic
**Tier:** 3 — Ecosystem Level
**Skill File:** `SKILL.md`
**Source:** YVYC Agentic Skill Library — built on principal-agent theory and
dynamic trust calibration research.

---

## What This Skill Does

Turns Claude into an agent reliability analyst that builds and applies structured
reputation tracking for AI agents and human-AI collaborators. Moves beyond static
role-based trust — "this agent is trusted because that's its job" — to dynamic,
evidence-based trust — "this agent has earned this level of trust based on what
it has actually demonstrated across these specific domains."

---

## When To Use It

- You need to decide how much authority to delegate to an agent based on its history
- An agent in your system keeps underperforming and you need a structured response
- You want to build a reputation system before problems emerge, not after
- You're scaling a multi-agent system and need trust levels to stay evidence-based
- You inherited an agent setup and don't know if the trust assignments are warranted

---

## How To Activate It

Once installed, activate this skill by saying something like:

> "Build a reputation profile for [agent name] based on this task history: [history]"

Other ways to trigger it:
- "Evaluate whether my research agent has earned its current trust level"
- "Track and score my agents' reliability over time"
- "This agent keeps failing at [task type] — how should that affect its authority?"
- "Build a reputation tracking system for my multi-agent pipeline"

---

## What To Provide

| Input | Required? | Example |
|---|---|---|
| Agent identifier | Yes | "Research agent" |
| Task history | Yes | "Completed 47 research tasks, 3 pulled from unauthorized sources, 2 returned incomplete data" |
| Trust domain | Yes | "Web research and source verification" |
| Current trust level | No | "Currently authorized to access any public web source autonomously" |
| Failure context | No | "The unauthorized source incidents occurred when primary sources were unavailable" |

---

## Example Usage

**You say:**
> "Build a reputation profile for my research agent. Task history: 47 completed
> research tasks over 3 months. 3 incidents of pulling from unauthorized sources.
> 2 incomplete data returns. 1 near-miss where it almost cited a retracted paper.
> Current trust level: autonomous access to any public web source. Domain: web
> research and source verification."

**Claude delivers:**
> A complete reputation profile showing the agent's baseline evidence vs. assumed
> trust, domain-specific reliability scores with trend direction, a specific finding
> that autonomous source access exceeds demonstrated reliability in source
> verification, trust calibration recommendations including conditional autonomy
> with source-type restrictions, and a maintenance protocol defining when the
> reputation is reviewed and how new incidents are weighted.

---

## Pro Tips

- Always run domain-specific reputation analysis — a single global score hides
  the most important information
- The trend direction matters as much as the current score — a low but improving
  agent may deserve more trust than a high but declining one
- Define your decay function early: how long should a past failure affect current
  trust? 30 days? 90 days? Task-count based? Build that in from the start
- Pair with `trust-calibration` to translate reputation scores into specific
  permission adjustments
- Revisit reputation profiles whenever an agent's task domain expands —
  past reliability in one domain does not transfer to a new one

---

## How This Fits The YVYC Agentic Stack

| Skill | Role in Stack |
|---|---|
| `delegation-network-mapper` | Maps the full authority structure |
| `reputation-signal` | Tracks and evaluates agent reliability over time (this skill) |
| `trust-calibration` | Sets appropriate trust levels based on reputation data |
| `permission-attenuation` | Enforces least-privilege based on calibrated trust |
| `monitoring-protocol` | Detects live performance signals for reputation updates |
| `accountability-chain` | Traces failures back to the responsible agent for scoring |

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
