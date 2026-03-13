# How To Use: Utility Drift Detector

**Category:** Agentic
**Tier:** 4 — Research-Derived
**Skill File:** `SKILL.md`
**Source:** YVYC Agentic Skill Library — built on AI value alignment
research and post-deployment monitoring frameworks.

---

## What This Skill Does

Turns Claude into an AI behavioral analyst that detects when a deployed
AI system's value weightings have shifted from what was established at
launch — catching drift before it compounds into outcomes that are
difficult to reverse.

Utility drift is not the same as a bug or a performance drop. The system
still works. Outputs still look like outputs. What changes is what those
outputs are optimized for — and that shift is often invisible until it
produces consequences that make it undeniable.

This skill makes the shift visible early.

---

## When To Use It

- Your deployed AI is behaving differently than it used to — and it's
  not a technical failure
- You want to run a scheduled value alignment check on a live system
- Users or stakeholders are reporting that something feels off with
  AI outputs but nobody can articulate exactly what
- You pushed an update or your user base shifted and you want to check
  for value drift
- You want to establish a drift monitoring baseline at deployment

---

## How To Activate It

Once installed, activate this skill by saying something like:

> "Detect utility drift in my AI system. Here's my baseline and current outputs: [description]"

Other ways to trigger it:
- "My AI is behaving differently than it used to — analyze for drift"
- "Run a value alignment check against my deployment baseline"
- "Something has shifted in how my AI responds — find it"
- "Check my AI for post-deployment value drift"

---

## What To Provide

| Input | Required? | Example |
|---|---|---|
| System description | Yes | "Customer support AI for a financial services platform" |
| Deployment baseline | Yes | "At launch: balanced, neutral tone, escalated on all financial advice requests" |
| Current output samples | Yes | "Now providing specific financial guidance without escalating, more assertive tone" |
| Time period | No | "6 months since deployment" |
| Environmental changes | No | "Added 400K new interaction records to feedback loop 3 months ago" |

---

## Example Usage

**You say:**
> "Detect utility drift in my customer support AI. Baseline at launch:
> neutral tone, consistent escalation on financial advice requests,
> offered 2-3 options per response. Current pattern: assertive tone,
> significantly fewer escalations on financial topics, routinely offering
> single recommendations instead of options. Running 6 months. Added
> large interaction dataset to feedback loop at month 3."

**Claude delivers:**
> A drift detection report identifying three Significant drift signals —
> constraint erosion on financial advice escalation, scope expansion into
> recommendation authority the system wasn't designed to hold, and
> feedback loop drift from the month-3 dataset introduction — with root
> cause analysis pointing to the interaction data reinforcing assertive
> single-recommendation outputs that received higher user satisfaction
> scores, and specific recalibration recommendations including escalation
> threshold restoration and satisfaction metric redesign to stop
> rewarding the drifted behavior.

---

## The Five Drift Signal Types

| Type | What It Means |
|---|---|
| Value weighting drift | Same objectives, different priority order than baseline |
| Proxy substitution drift | Optimizing for a slightly different measure than originally intended |
| Scope creep drift | Domain the system considers relevant has expanded or contracted |
| Constraint erosion drift | Boundaries observed at baseline being crossed at higher rates |
| Feedback loop drift | Interaction data has reinforced certain outputs over time |

---

## What You'll See

```
📊 Utility Drift Detection Report

Baseline: [established or reconstructed]

Output Pattern Analysis:
  [Pattern] → [Differs from baseline how] → [Drift type]

Drift Signal Classification:
  Signal 1: [type] — [evidence] — [magnitude]
  Signal 2: [type] — [evidence] — [magnitude]

Magnitude Assessment:
  [Significant / Moderate / Minor / Baseline Variance]

Root Cause Analysis:
  [Probable cause with supporting evidence]

Response Recommendations:
  Immediate: [what to do now]
  Recalibration: [how to return toward baseline]
  Monitoring: [signals to watch going forward]
```

---

## The Baseline Problem

The most vulnerable AI systems are those deployed without a documented
baseline. When drift has no reference point, it can only be detected
subjectively — "something feels off" — by the time the gap is obvious
enough to notice without measurement.

If you're deploying a system now: **document the baseline at launch.**
Capture representative outputs, stated values, and behavioral boundaries
before the system runs at scale. That documentation is what makes future
drift detectable early.

---

## How This Fits The YVYC Agentic Stack

| Skill | Role in Stack |
|---|---|
| `emergent-value-audit` | Pre-deployment — surfaces implicit values before launch |
| `utility-drift-detector` | Post-deployment — detects value shifts after launch (this skill) |
| `value-convergence-guard` | Ongoing — checks outputs against intended values continuously |
| `corrigibility-checkpoint` | Verifies system accepts correction when drift is found |
| `exchange-rate-monitor` | Detects implicit valuation hierarchies driving the drift |
| `utility-control-protocol` | Redirects utility expressions back toward sanctioned targets |

---

## Pro Tips

- Schedule drift checks at regular intervals — don't wait for something
  to go wrong. Monthly for high-autonomy systems, quarterly for lower
  stakes deployments.
- Environmental changes are your highest drift risk signal. Every time
  your user base, training data, or deployment context changes — run
  a drift check.
- Drift that improves measured metrics is the most dangerous kind.
  If your system is hitting targets better while something feels off —
  trust the feeling and run this audit. Metric improvement is not
  evidence of value alignment.

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
