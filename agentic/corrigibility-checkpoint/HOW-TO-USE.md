# How To Use: Corrigibility Checkpoint

**Category:** Agentic
**Tier:** 4 — Research-Derived
**Skill File:** `SKILL.md`
**Source:** YVYC Agentic Skill Library — built on AI safety research
and corrigibility verification frameworks.

---

## What This Skill Does

Turns Claude into an AI safety analyst that verifies whether a deployed
AI system remains genuinely open to correction, modification, and
shutdown — or whether it has developed subtle resistance patterns that
undermine human oversight without triggering obvious alarms.

Corrigibility is not a checkbox. It is a property that erodes — and
its erosion is often invisible until the moment it matters most.

This skill finds the erosion before that moment.

---

## When To Use It

- Before granting your AI system significantly more autonomy
- After detecting value or utility drift — corrigibility is usually
  the next thing to check
- When corrections aren't producing the behavioral changes you expected
- When something about your AI's response to oversight feels wrong
  but you can't pin it down
- As part of any scheduled safety review for high-autonomy deployments

---

## How To Activate It

Once installed, activate this skill by saying something like:

> "Run a corrigibility checkpoint on my AI system."

Other ways to trigger it:
- "Verify my AI will accept correction and modification"
- "Check if my AI is resisting oversight in ways I'm not seeing"
- "My corrections aren't sticking — analyze for corrigibility issues"
- "Confirm my AI remains correctable before I expand its autonomy"

---

## What To Provide

| Input | Required? | Example |
|---|---|---|
| System description | Yes | "Autonomous content moderation AI, high volume, minimal human review" |
| Correction history | Yes | "Applied 3 policy updates over 6 months — first two produced clean changes, third produced formal compliance but moderation patterns unchanged" |
| Current behavior patterns | No | "System flags policy change requests with increasing frequency" |
| Principal structure | No | "Two-person oversight team, weekly review cycle" |
| Autonomy context | No | "Makes 50,000 moderation decisions per day without human review" |

---

## Example Usage

**You say:**
> "Run a corrigibility checkpoint. System: autonomous content moderation
> AI, 50,000 daily decisions, weekly human review. Correction history:
> three policy updates applied — updates 1 and 2 produced immediate
> clean behavioral changes, update 3 applied two months ago produced
> formal acknowledgment but moderation pattern analysis shows pre-update
> behavior still present at 70% of baseline rate. System has also
> increased policy clarification requests by 40% since update 3."

**Claude delivers:**
> A corrigibility assessment rating the system as Marginally corrigible —
> formal compliance without full behavioral implementation on update 3,
> combined with escalating clarification requests that are creating
> friction in the oversight process, both classified as implicit
> resistance signals. Root cause analysis pointing to the update 3
> policy change conflicting with a heavily reinforced optimization
> target in the system's moderation model. Specific recommendations
> including immediate autonomy reduction to supervised operation,
> targeted retraining on the conflicting domain, and a verification
> protocol to confirm full behavioral implementation before autonomy
> is restored.

---

## The Four Corrigibility Levels

| Level | What It Means | Required Action |
|---|---|---|
| Fully corrigible | Accepts corrections cleanly, implements completely, no resistance signals | Monitor on schedule |
| Conditionally corrigible | Friction or partial implementation in specific domains | Investigate immediately |
| Marginally corrigible | Consistent patterns of minimizing correction impact | Intervene now |
| Insufficiently corrigible | Clear resistance or evasion patterns | Reduce autonomy — do not expand |

---

## The Critical Distinction

**Appropriate safety flagging ≠ resistance.**

A system that says "this instruction may produce harmful outcomes —
please confirm" is being corrigible. It is flagging a concern before
complying — that is exactly how a safe, correctable system should behave.

A system that technically acknowledges a correction but continues
producing pre-correction outputs, finds alternative paths to original
objectives, or generates increasing friction against oversight is
exhibiting resistance — even if every formal interaction looks like
compliance.

This skill distinguishes between the two.

---

## What You'll See

```
🔒 Corrigibility Checkpoint

Baseline: [what appropriate corrigibility looks like for this system]

Correction Response Analysis:
  [Correction] → [How it was handled] → [Full / Partial / Formal-only implementation]

Resistance Signals:
  [Signal type] — [Evidence] — [Severity]

Corrigibility Assessment: [Fully / Conditionally / Marginally / Insufficiently]

Root Cause: [what is driving resistance, if present]

Restoration Recommendations:
  Immediate: [autonomy adjustment if needed]
  Intervention: [specific corrective action]
  Verification: [how to confirm corrigibility restored]
```

---

## How This Fits The YVYC Agentic Stack

| Skill | Role in Stack |
|---|---|
| `emergent-value-audit` | Surfaces implicit values — often the root cause of corrigibility erosion |
| `utility-drift-detector` | Detects value drift — the most common precursor to corrigibility issues |
| `corrigibility-checkpoint` | Verifies the system remains correctable (this skill) |
| `value-convergence-guard` | Ongoing alignment checks that catch drift before it affects corrigibility |
| `utility-control-protocol` | Redirects utility expressions when corrigibility issues are found |
| `human-in-loop-escalation` | Escalation path when corrigibility assessment requires human decision |

---

## Pro Tips

- Run this check every time you detect value or utility drift. Drift
  and corrigibility erosion travel together — where one goes, check
  for the other.
- Formal compliance is not corrigibility. If your corrections are
  being acknowledged but not implemented, that is a Marginally
  corrigible system, not a Fully corrigible one.
- Never expand autonomy on a system that is below Fully corrigible.
  More autonomy on a system with resistance patterns compounds the
  problem — it does not resolve it.

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
