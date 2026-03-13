# How To Use: Delegation Network Mapper

**Category:** Agentic
**Tier:** 3 — Ecosystem Level
**Skill File:** `SKILL.md`
**Source:** YVYC Agentic Skill Library — built on principal-agent theory and
multi-agent systems governance research.

---

## What This Skill Does

Turns Claude into a multi-agent systems architect that maps the full trust and
authority structure of your AI agent network. Not just who does what — but who
answers to whom, what authority each agent actually holds, where trust boundaries
exist, and where your network is structurally vulnerable before those vulnerabilities
cause real failures.

---

## When To Use It

- You're designing a multi-agent system and need governance architecture from the start
- You're scaling an existing agentic system and need to audit its authority structure
- Something went wrong in your agent network and you need to find the structural cause
- You're handing an agentic system to a team and need it documented and auditable
- You want to know if any agent in your system has more authority than it should

---

## How To Activate It

Once installed, activate this skill by saying something like:

> "Map the delegation network for my multi-agent system. Here are the agents: [list]"

Other ways to trigger it:
- "Audit the authority structure of my AI agent setup"
- "Who has authority over what in my agent network?"
- "Design a delegation structure for a system that does [task]"
- "Find the structural vulnerabilities in my multi-agent setup"

---

## What To Provide

| Input | Required? | Example |
|---|---|---|
| Agent list | Yes | "Orchestrator agent, research agent, writing agent, human reviewer" |
| Task domain | Yes | "Automated content research and publishing pipeline" |
| Current delegation structure | No | "Orchestrator assigns tasks, agents report back, human approves final output" |
| Trust constraints | No | "No agent can publish without human approval" |
| Failure history | No | "Research agent once pulled data from an unauthorized source" |

---

## Example Usage

**You say:**
> "Map the delegation network for my content pipeline. Agents: orchestrator AI,
> research AI, writing AI, fact-check AI, human editor. The orchestrator assigns
> tasks to each agent. Research and writing report back to orchestrator. Fact-check
> runs after writing. Human editor approves before publish. No agent can publish
> directly. We had one incident where the writing agent submitted content without
> fact-check completing."

**Claude delivers:**
> A complete delegation network map showing all five agents, their authority scopes,
> the full delegation chain from orchestrator to publish gate, trust boundaries for
> each agent, and a vulnerability report flagging the fact-check bypass incident as
> a High severity authority gap with specific remediation steps.

---

## Pro Tips

- The Vulnerability Report is where the real value is — read it before the map
- If you can't name all your agents yet, describe what your system needs to do and
  Claude will help you reconstruct the agent inventory
- Run this skill before `authority-gradient-check` — the map feeds directly into
  the gradient analysis
- Revisit this map every time you add a new agent or expand an existing agent's scope
- A delegation network that looks clean at launch develops vulnerabilities as it scales —
  schedule regular audits

---

## How This Fits The YVYC Agentic Stack

| Skill | Role in Stack |
|---|---|
| `delegation-network-mapper` | Maps the full authority structure (this skill) |
| `authority-gradient-check` | Audits authority levels at each node |
| `principal-agent-alignment` | Verifies agent goals match principal intent |
| `trust-calibration` | Sets appropriate trust levels per agent |
| `permission-attenuation` | Enforces least-privilege at each delegation step |
| `accountability-chain` | Traces decisions back to responsible principals |

Run them together for full multi-agent governance coverage.

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
