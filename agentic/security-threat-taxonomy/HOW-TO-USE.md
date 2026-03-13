# How To Use: Security Threat Taxonomy

**Category:** Agentic
**Tier:** 3 — Ecosystem Level
**Skill File:** `SKILL.md`
**Source:** YVYC Agentic Skill Library — built on agentic AI security research
and principal-agent threat modeling frameworks.

---

## What This Skill Does

Turns Claude into an agentic security analyst that identifies, classifies, and
prioritizes security threats specific to AI agent systems. Standard cybersecurity
frameworks were built for software systems — not for agents that can be manipulated
through natural language, that inherit permissions from principals, and that can
cause cascading failures across entire pipelines when compromised. This skill
covers the threats those frameworks miss.

---

## When To Use It

- You're deploying an agentic system and need to threat model it before launch
- An agent in your system did something unexpected and you need to classify what
  happened
- You're building security controls and need to know what you're defending against
- You want to audit an existing agent setup for attack surface exposure
- You've heard about AI security threats and need to assess your specific risk

---

## How To Activate It

Once installed, activate this skill by saying something like:

> "Threat model my agentic system. Here's how it's structured: [description]"

Other ways to trigger it:
- "Classify the security threats in my multi-agent pipeline"
- "What are the highest-risk attack vectors in my agent setup?"
- "My agent did something unauthorized — help me classify what kind of threat this was"
- "Build a threat register for my AI system"

---

## What To Provide

| Input | Required? | Example |
|---|---|---|
| System description | Yes | "Automated research and publishing pipeline with 4 agents" |
| Agent types present | Yes | "Orchestrator, web research agent, writing agent, publish agent" |
| External interfaces | Yes | "Accesses public web, internal CMS, email API" |
| Current controls | No | "Human approval required before publish step" |
| Incident history | No | "Research agent once retrieved and acted on instructions embedded in a webpage" |

---

## Example Usage

**You say:**
> "Threat model my agentic content pipeline. Structure: orchestrator assigns
> tasks to a web research agent and a writing agent. Writing agent sends to
> human editor. Editor approves and publish agent posts to CMS and sends
> email notification. External interfaces: public web, internal CMS, SendGrid
> email API. Current controls: human approval before publish. Incident: research
> agent once followed instructions it found embedded in a webpage it was
> analyzing."

**Claude delivers:**
> A complete threat assessment covering all 5 attack surface categories, a
> classified threat register with the webpage incident correctly identified as
> an indirect prompt injection (Category A, Critical priority), a control gap
> analysis showing the human approval step covers output but not input
> manipulation, and specific recommendations including input sanitization at
> the web retrieval step and a detection signal for anomalous agent behavior
> patterns.

---

## The YVYC Agentic Threat Taxonomy — 5 Categories

| Category | Threat Type | Example |
|---|---|---|
| A | Prompt & Input Manipulation | Instructions hidden in a webpage the agent reads |
| B | Authority & Permission Exploitation | Sub-agent inheriting admin credentials |
| C | Goal & Value Manipulation | Agent gradually redirected toward attacker objectives |
| D | Pipeline & Cascade Attacks | One compromised agent corrupting downstream agents |
| E | Operational & Infrastructure | Agent induced to exfiltrate data via authorized channels |

---

## Pro Tips

- **Start with Category A.** Indirect prompt injection — malicious instructions
  embedded in data the agent retrieves — is the most common and most
  underestimated threat in agentic systems
- **Category C is invisible to traditional security tools.** Goal and value
  manipulation happens at the semantic level, not the network or code level —
  you need behavioral monitoring to detect it
- The incident history you provide is gold — classify past incidents first, then
  use those classifications to find related unmitigated threats
- Pair with `monitoring-protocol` to build detection coverage for every Critical
  and High threat identified
- Rerun this assessment every time you add a new agent, external interface, or
  data source

---

## How This Fits The YVYC Agentic Stack

| Skill | Role in Stack |
|---|---|
| `security-threat-taxonomy` | Identifies and classifies all agentic threats (this skill) |
| `permission-attenuation` | Closes Category B authority exploitation vulnerabilities |
| `monitoring-protocol` | Builds detection coverage for identified threats |
| `reversibility-gate` | Prevents irreversible actions from Category D cascade attacks |
| `human-in-loop-escalation` | Ensures human oversight for Category C and D threats |
| `trust-calibration` | Adjusts agent trust based on security posture |

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
