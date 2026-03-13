# How To Use: Accountability Chain

**Category:** Agentic
**Tier:** 3 — Ecosystem Level
**Skill File:** `SKILL.md`
**Source:** YVYC Agentic Skill Library — built on AI governance frameworks and
principal-agent accountability theory.

---

## What This Skill Does

Turns Claude into an AI governance analyst that establishes, traces, and enforces
accountability across multi-agent AI decision chains. When AI agents make decisions
autonomously, "the AI did it" becomes a structural escape hatch that lets failures
go unowned and uncorrected. This skill closes that gap — it maps every decision
to an accountable human, defines what must be logged to make that accountability
traceable, and builds the post-incident trace protocol so that when something
goes wrong, responsibility has a clear path back to its source.

---

## When To Use It

- You're deploying an agentic system and need accountability built in before launch
- An AI-driven outcome went wrong and you need to trace who is responsible
- You need an audit trail framework for compliance, legal, or organizational purposes
- Your current system produces outcomes where ownership is genuinely unclear
- You want to make sure "the AI decided" is never an accepted answer in your system

---

## How To Activate It

Once installed, activate this skill by saying something like:

> "Build an accountability chain for my agentic system. Here's how decisions flow: [description]"

Other ways to trigger it:
- "Trace accountability for this AI-driven failure: [incident description]"
- "Who is responsible for what my agent did?"
- "Design an audit trail framework for my multi-agent pipeline"
- "Find the accountability gaps in my AI system"

---

## What To Provide

| Input | Required? | Example |
|---|---|---|
| System description | Yes | "Automated loan pre-screening pipeline using 3 AI agents" |
| Agent and human roles | Yes | "Data agent, scoring agent, decision agent, human loan officer final review" |
| Decision types | Yes | "Credit data retrieval, risk scoring, approve/decline recommendation" |
| Existing audit mechanisms | No | "Decision outputs are logged but not reasoning or inputs" |
| Incident details | No | "A borderline application was declined, applicant disputes the decision" |

---

## Example Usage

**You say:**
> "Build an accountability chain for my loan pre-screening system. Agents: data
> retrieval agent pulls credit data, scoring agent generates risk score, decision
> agent produces approve/decline recommendation. Human loan officer reviews
> recommendation and makes final decision. Current audit: we log the final
> decision and the risk score but not the data inputs or reasoning. Incident:
> an applicant is disputing a decline and we can't reconstruct why the scoring
> agent produced the score it did."

**Claude delivers:**
> A complete accountability framework assigning primary accountability to the
> loan officer for the final decision, delegating accountability to the system
> designer for the scoring criteria, oversight accountability to the loan officer
> for catch failures on the recommendation, and a critical audit gap finding that
> the missing input and reasoning logs make the dispute legally and operationally
> unresolvable. Includes specific audit trail requirements for each agent and a
> failure trace protocol for the current incident.

---

## The Four Accountability Layers

Every decision in an agentic system has four accountability layers. This skill
maps all four — not just the most visible one.

| Layer | Who | Accountable For |
|---|---|---|
| Primary | Decision-maker | The specific decision and its direct outcome |
| Delegating | Authorizing principal | The framework that permitted this class of decision |
| Oversight | Reviewer | Failing to catch errors within their review scope |
| Systemic | System designer/deployer | Structural conditions that shaped the decision context |

---

## Pro Tips

- If you can't name a specific human for primary accountability at any decision
  point — that's your most critical gap. Find it and fix it before deployment.
- "Human in the loop" only means something if the audit trail proves the human
  actually reviewed the decision — presence is not accountability
- The dispute scenario is your best test: if an affected party challenges a
  decision, can you reconstruct exactly what happened and who is responsible?
  If not, your audit trail is insufficient.
- Accountability chains should be reviewed every time a new agent is added,
  a new decision type is introduced, or a new human role is involved
- Pair with `delegation-network-mapper` — authority and accountability are
  two sides of the same governance coin

---

## How This Fits The YVYC Agentic Stack

| Skill | Role in Stack |
|---|---|
| `accountability-chain` | Traces decisions to responsible principals (this skill) |
| `delegation-network-mapper` | Maps who holds authority at each decision point |
| `monitoring-protocol` | Captures the real-time audit trail accountability requires |
| `human-in-loop-escalation` | Ensures humans are genuinely in the loop, not nominally |
| `verifiable-completion` | Confirms decisions were completed as authorized |
| `principal-agent-alignment` | Verifies agent actions match principal intent |

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
