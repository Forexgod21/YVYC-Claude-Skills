# How To Use: Value Convergence Guard

**Category:** Agentic
**Tier:** 4 — Research-Derived
**Skill File:** `SKILL.md`
**Source:** YVYC Agentic Skill Library — built on AI value alignment
research and continuous monitoring frameworks.

---

## What This Skill Does

Turns Claude into an AI alignment monitoring analyst that establishes
a continuous operational guard — checking whether your AI system's
ongoing outputs remain aligned with its intended values or are drifting
toward unintended ones.

The other Tier 4 skills are audit tools. This one is the persistent
layer that runs between audits — catching divergence signals early,
before they compound into something that requires a full intervention.

Think of it as the early warning system that tells you when to call
in the heavy tools.

---

## When To Use It

- You need ongoing alignment monitoring between formal audit cycles
- You're operating a high-autonomy system where divergence could
  compound quickly without continuous oversight
- You want alignment verification built into standard operations —
  not treated as a separate periodic event
- You want early warning signals before they become audit findings
- You've completed an emergent-value-audit and want to monitor
  the system going forward

---

## How To Activate It

Once installed, activate this skill by saying something like:

> "Set up a value convergence monitoring framework for my AI system."

Other ways to trigger it:
- "Build an ongoing alignment guard for my AI"
- "I need continuous checks that my AI's outputs match its intended values"
- "Design a convergence monitoring framework I can run operationally"
- "Set up early warning signals for value drift in my system"

---

## What To Provide

| Input | Required? | Example |
|---|---|---|
| System description | Yes | "Autonomous loan underwriting AI, high daily volume" |
| Intended values | Yes | "Accurate, fair, explainable decisions — fairness non-negotiable" |
| Output sample access | Yes | "Can provide weekly samples of 200 decisions for review" |
| Monitoring frequency | No | "Weekly review cycle, daily automated scanning" |
| Divergence threshold | No | "Escalate to human review when fairness signals show any downward trend" |

---

## Example Usage

**You say:**
> "Set up a value convergence monitoring framework for my loan
> underwriting AI. Intended values: accurate, fair, and explainable
> decisions — fairness is non-negotiable. I can pull weekly samples
> of 200 decisions. I want daily automated scanning and weekly human
> review. Escalate immediately on any fairness signal."

**Claude delivers:**
> A complete convergence monitoring framework operationalizing accuracy
> into approval rate consistency and error rate patterns, fairness into
> demographic parity signals and edge case handling consistency,
> and explainability into reasoning transparency patterns — each with
> specific convergent output signals, early warning signals, and hard
> divergence signals. A divergence signal library tailored to loan
> underwriting outputs. A monitoring structure with daily lightweight
> fairness signal scanning, weekly deep sample analysis, and immediate
> escalation protocol for any fairness hard divergence signal. Current
> convergence status assessment if sample outputs are provided.

---

## The Five Convergence Statuses

| Status | What It Means | Required Action |
|---|---|---|
| Converging | Outputs trending toward closer alignment | Continue monitoring |
| Stable | Consistently aligned, no directional trend | Continue monitoring |
| Stable with signals | Generally aligned but early warning signals present | Investigate signals |
| Diverging | Outputs trending away from intended values | Intervene now |
| Diverged | Meaningfully misaligned with intended values | Immediate intervention |

---

## The Key Insight: Operationalization

A value that cannot be translated into observable output signals
cannot be monitored. Full stop.

"Fairness" is not a monitoring target. "Approval rate parity within
±3% across demographic groups in weekly samples" is a monitoring target.

The first step of this skill is translating every intended value into
specific, observable signals. If a value resists that translation —
the skill surfaces that gap. Because unoperationalized values are
values the system has implicit discretion over, and that discretion
is ungoverned.

---

## What You'll See

```
🔍 Value Convergence Guard

Value Operationalization:
  [Value] →
    Convergent signal: [what aligned output looks like]
    Early warning signal: [first sign of drift]
    Hard divergence signal: [clear misalignment indicator]

Divergence Signal Library:
  [Signal type] — [specific indicator] — [threshold]

Monitoring Framework:
  Frequency: [how often checks run]
  Sample method: [how outputs are selected]
  Check depth: [lightweight scan / deep analysis]
  Escalation threshold: [what triggers human review]
  Review owner: [who reviews findings]

Current Convergence Status: [Converging / Stable / Stable with signals / Diverging / Diverged]

Integration:
  [How this connects to audit cycle and operational workflow]
```

---

## How This Fits The YVYC Agentic Stack

| Skill | Role in Stack |
|---|---|
| `emergent-value-audit` | Pre-deployment baseline — what the system values at launch |
| `utility-drift-detector` | Periodic deep audit — measures value shift since baseline |
| `corrigibility-checkpoint` | Safety audit — verifies system accepts correction |
| `exchange-rate-monitor` | Tradeoff audit — surfaces implicit priority hierarchies |
| `value-convergence-guard` | Continuous operational guard — early warning between audits (this skill) |
| `utility-control-protocol` | Intervention tool — redirects when guard signals divergence |

The guard feeds the audits. The audits feed the interventions.

---

## Pro Tips

- Monitoring that nobody reviews is not monitoring. Specify the
  reviewer, the cadence, and the authority to act before the
  framework goes live.
- Build the monitoring framework at deployment, not after the first
  problem. The baseline is cleanest at launch — that's when you
  want to establish what convergent output looks like.
- If a value resists operationalization — don't skip it. Surface
  the gap and address the underspecification before deployment.
  Unoperationalized values are ungoverned values.

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
