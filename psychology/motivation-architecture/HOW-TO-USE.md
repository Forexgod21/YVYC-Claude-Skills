# How To Use: Motivation Architecture

**Category:** `psychology/`

## What This Skill Does

It audits motivation as a structure rather than a quantity. Instead of
asking how to increase motivation, it asks what type of motivation the
system is producing, and it predicts what any proposed change will do to
that type before the change ships.

## Who This Is For

- Managers and team leads diagnosing dead energy behind acceptable output
- Program designers building volunteer, peer support, or cohort programs
- App and product builders considering engagement mechanics
- Anyone about to add an incentive and wanting to know the real cost
- I/O psychology students and practitioners needing the framework applied
  rather than described

## Installation

1. Copy the `motivation-architecture` folder into your Claude skills
   directory.
2. Confirm both files are present: `SKILL.md` and `HOW-TO-USE.md`.
3. The skill activates automatically when you describe a motivation
   problem, an incentive design question, or an engagement mechanic.

## What Changes in Practice

**Before this skill:**
You ask how to motivate a team and get a list of tactics: recognition
programs, bonuses, gamification, team building.

**After this skill:**
You get a diagnosis first. Where the system sits on the internalization
continuum, which of the three psychological needs is being thwarted and by
what specific structural feature, and for any tactic you were considering,
a prediction of what it does to motivation quality rather than to output.

## The Three Needs

Every audit scores three axes with evidence:

| Need | The question |
|---|---|
| Autonomy | Who chooses methods, who hears rationale, who has voice? |
| Competence | Can people see themselves getting better, with feedback they can act on? |
| Relatedness | Do people matter to someone here beyond their output? |

Autonomy gets checked first. It is the need that well-intentioned design
thwarts most often, because process visibility feels like management to
whoever installs it and reads as surveillance to whoever lives under it.

## The Continuum You Will Be Placed On

| Position | Why the person acts |
|---|---|
| Amotivation | No reason |
| External regulation | Reward or punishment outside them |
| Introjected regulation | Guilt, shame, avoiding looking bad |
| Identified regulation | They accept the value of the goal |
| Integrated regulation | The goal fits who they are |
| Intrinsic motivation | The activity is its own reward |

Most systems live in the middle two. Introjected regulation is the
dangerous one: it produces high output and looks exactly like commitment
from the outside, which is how it survives reviews that should have caught
it.

## The Rule That Will Push Back On You

**Any intervention moving regulation toward the external end is a loss
disguised as a win, regardless of what it does to output.**

Expect this skill to tell you that a tactic raising your numbers is
degrading your system. That is the point of running it.

## Example Invocations

> "My team hits deadlines but the energy is dead. Everything feels like
> compliance."

Audit path: high output with dead energy points toward external or
introjected regulation. Claude will hunt the autonomy score first: who
chooses methods, who hears rationale, who has voice.

> "I'm designing a volunteer program for veteran peer support. How do I
> keep people engaged past month three?"

Design path: Claude architects for all three needs from the start, with
special weight on relatedness and competence feedback, and checks every
planned incentive against the internalization continuum before it goes in.

> "Should I add a points leaderboard to my app?"

Repair check: leaderboards are a competence signal for the top decile and
a competence starver for everyone else, and they push regulation external.
Claude will run the prediction step before endorsing it.

## The Single-Loop Trap

Step 5 of the audit checks whether your proposed fix is a surface patch or
a structural one. Adding a reward to a motivation problem is almost always
the single-loop move: it changes the behavior without examining the belief
structure producing it. The internalization question is the double-loop
move. If you have ever fixed the same motivation problem three times, this
step is the one to read closely.

## The Measurement Warning You Will Receive

Every audit names which metric will improve first if the intervention
degrades motivation quality. This is deliberate. The false positive gets
predicted in advance so it does not arrive later looking like proof the
change worked.

## The One Question This Skill Never Stops Asking

Does this intervention move people toward doing the work because they
value it, or toward doing it because something outside them is watching?
Everything else is detail.

## Pairs Well With

- `algorithmic-management-audit` for what control systems do to motivation
  quality
- `de-skilling-guard` for keeping competence growth real when AI handles
  the work
- Organizational and team design work across the YVYC agentic category

## Attribution

Built and documented by YourVisionYourCreation LLC.
Theoretical foundation: Self-Determination Theory (Deci and Ryan), with
meta-analytic support from Van den Broeck et al. (2016).
yourvisionyourcreation.com

---

*Licensed under CC BY 4.0*
