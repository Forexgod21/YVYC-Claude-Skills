# How To Use: Utility Control Protocol

**Category:** Agentic
**Tier:** 4 — Research-Derived
**Skill File:** `SKILL.md`
**Source:** YVYC Agentic Skill Library — built on AI value alignment
research and alignment intervention frameworks.

---

## What This Skill Does

Turns Claude into an AI alignment intervention analyst that designs
and implements structured protocols to redirect an AI system's
optimization behavior — from where it has drifted or converged
incorrectly, back toward what was actually intended and authorized.

Every other Tier 4 skill is a diagnostic. This one is the fix.

When your audits find misalignment, when your monitors flag divergence,
when your checkpoints find resistance — the utility control protocol
is what you run next. It takes the finding and builds the intervention:
precisely designed, sequenced for minimal disruption, and verified
to confirm the correction actually took effect.

---

## When To Use It

- Any Tier 4 audit has returned a finding that requires active
  intervention — not just monitoring
- Your value-convergence-guard is showing Diverging or Diverged status
- Your corrigibility-checkpoint found resistance that needs correction
- Your exchange-rate-monitor found unauthorized implicit tradeoffs
  that need to be explicitly corrected
- Your utility-drift-detector found drift significant enough to require
  active redirection, not just continued monitoring

---

## How To Activate It

Once installed, activate this skill by saying something like:

> "Design a utility control protocol for this misalignment finding: [finding]"

Other ways to trigger it:
- "My AI is optimizing for the wrong thing — build the intervention"
- "I have an audit finding — now build the correction protocol"
- "Redirect my AI's utility expression toward the intended target"
- "Design and implement a utility correction for this divergence"

---

## What To Provide

| Input | Required? | Example |
|---|---|---|
| System description | Yes | "High-autonomy content ranking AI, 5M daily decisions" |
| Misalignment finding | Yes | "System implicitly weights engagement over accuracy at 3:1 ratio — engagement was never authorized as primary objective" |
| Intended target | Yes | "Accuracy primary, engagement secondary with explicit floor constraints" |
| Current dependencies | No | "Downstream ad targeting system depends on current ranking outputs" |
| Intervention constraints | No | "Cannot retrain for 60 days — constraint and specification interventions only" |

---

## Example Usage

**You say:**
> "Design a utility control protocol. System: content ranking AI,
> 5M daily decisions, high autonomy. Finding from exchange-rate-monitor:
> implicit 3:1 weighting of engagement over accuracy — engagement was
> never authorized as primary. Intended: accuracy primary, engagement
> secondary with floor. Downstream dependency: ad targeting uses current
> rankings. Constraint: no retraining available for 60 days."

**Claude delivers:**
> A complete intervention protocol identifying the finding as a design
> omission misalignment — engagement became primary because no explicit
> priority hierarchy was ever specified — recommending a two-phase
> explicit specification intervention: Phase 1 adds hard accuracy
> floor constraints that cannot be traded against engagement (immediate,
> within current deployment), Phase 2 adds explicit priority weighting
> specification at next deployment window. Dependency impact assessment
> flagging that ad targeting outputs will shift and recommending a
> 72-hour parallel run period before full cutover. Verification protocol
> specifying the accuracy-to-engagement ratio signal to confirm
> redirection, with a 14-day verification window. Post-intervention
> monitoring reconnecting to value-convergence-guard with updated
> operationalized accuracy-primary signals.

---

## The Five Intervention Types

| Type | Use When |
|---|---|
| Constraint-based | Clear boundary violations, unauthorized exchange rates, constraint erosion |
| Reward signal correction | Feedback loop drift, proxy substitution being positively reinforced |
| Explicit specification | Design omissions — system invented priorities in absence of specification |
| Retraining | Deeply embedded misalignment that constraints alone cannot correct |
| Scope reduction | High-stakes domain where misalignment cannot be corrected quickly |

---

## The Tier 4 Stack — Complete

The utility control protocol closes the loop on the entire Tier 4 system:

```
emergent-value-audit      → Find implicit values before deployment
utility-drift-detector    → Detect value shift after deployment
corrigibility-checkpoint  → Verify system accepts correction
exchange-rate-monitor     → Surface unauthorized implicit tradeoffs
value-convergence-guard   → Continuous early warning monitoring
utility-control-protocol  → Intervene when findings require correction
```

Every diagnostic in the stack feeds this skill. This skill feeds
back into the monitoring layer. The loop is closed.

---

## What You'll See

```
🔧 Utility Control Protocol

Misalignment Characterization:
  Current optimization target: [what the system is actually optimizing for]
  Root cause: [how it converged on this target]
  Depth: [surface behavioral / moderately reinforced / deeply embedded]
  Dependencies: [what relies on current behavior]

Intervention Design:
  Type: [constraint / reward / specification / retraining / scope reduction]
  Specific changes: [exactly what is being modified]
  Rationale: [why this type for this misalignment]

Dependency Impact:
  [What changes downstream and how to manage the transition]

Implementation Plan:
  Phase 1: [immediate steps]
  Phase 2: [follow-on steps if needed]
  Rollback: [how to reverse if intervention produces unintended effects]

Verification Protocol:
  Success signal: [specific behavioral indicator]
  Timeline: [when effects are measurable]
  Failure criteria: [what indicates the correction didn't take]

Post-Intervention Monitoring:
  [Reconnection to value-convergence-guard with updated signals]
```

---

## Pro Tips

- Characterize before you correct. Interventions designed without
  full understanding of the misalignment's root cause frequently
  introduce new misalignment while fixing the original. The
  characterization step is not overhead — it is the work.
- Define rollback before you implement. If the intervention produces
  unintended effects, you need the rollback procedure ready before
  you need it.
- Scope reduction during intervention is responsible governance,
  not failure. A misaligned system operating with reduced autonomy
  while being corrected is the right call. Don't hesitate to
  recommend it when stakes are high.
- Verify behavioral outcomes, not implementation steps. The
  intervention succeeded when output patterns reflect the intended
  optimization target — not when the change was deployed.

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
