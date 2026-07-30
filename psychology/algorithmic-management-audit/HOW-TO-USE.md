# How To Use: Algorithmic Management Audit

**Category:** `psychology/`

## What This Skill Does

It audits any system where software directs, evaluates, or disciplines
human work. It identifies what the system actually does regardless of what
the features are called, tests whether workers can see and contest
decisions that affect them, and names the gray areas the system is
resolving silently at scale.

## Who This Is For

- Product and engineering teams building tools that manage or score people
- Operators running gig, contractor, or distributed workforces
- HR and I/O practitioners reviewing an algorithmic management deployment
- Anyone building agentic systems that assign work to humans
- Researchers needing the control framework applied rather than summarized

## Installation

1. Copy the `algorithmic-management-audit` folder into your Claude skills
   directory.
2. Confirm both files are present: `SKILL.md` and `HOW-TO-USE.md`.
3. The skill activates automatically when you describe a system that
   directs, monitors, scores, or schedules human work.

## What Changes in Practice

**Before this skill:**
You describe an AI scoring feature and get a technical review: model
accuracy, bias in training data, latency. The management functions inside
the feature never get examined as management.

**After this skill:**
Claude runs six audit lanes and returns structured findings: which control
functions the system actually exercises regardless of what they are called,
where a worker cannot see, understand, or contest a decision that affects
their pay, what the metrics will get gamed into, whether the human
override is real or decorative, and which gray-area judgment calls the
system is resolving silently that should escalate to a human.

## The Six Functions Being Inventoried

| Function | What it does |
|---|---|
| Restricting | Limits what options a worker can see or take |
| Recommending | Steers choices without formally requiring them |
| Recording | Captures worker activity as data |
| Rating | Scores the worker |
| Replacing | Substitutes automated judgment for human judgment |
| Rewarding | Distributes pay, access, or opportunity from the above |

Functions get identified by behavior, never by feature name. A feature
called "smart routing" that sends the best work to high scorers is
performing reward and restriction whether anyone called it that or not.

## Example Invocations

> "We're adding an AI feature that scores our support reps on call quality
> and routes the best leads to top scorers."

That is rating plus rewarding in one mechanism. Claude will audit the
score's transparency, the appeal path, the gaming surface (what behavior
maximizes the score without serving the customer), and the compounding
effect of routing opportunity toward yesterday's winners.

> "Audit how this gig platform manages its drivers."

Full six-lane audit from the worker's side: asymmetry inventory, silent
gray areas, contestability testing, findings with severity.

> "My agentic system assigns tasks to human reviewers. Anything I should
> worry about?"

Yes: the moment an agent directs human work, it is a manager. Claude runs
the design-time audit and applies the escalation rule to every gray area
the agent would otherwise resolve alone.

## The Contestability Test You Will Be Held To

Three questions per decision affecting pay, scheduling, or standing:

1. Can the worker **see** the decision was made?
2. Can the worker **understand** its basis?
3. Can the worker **contest** it to someone able to reverse it?

All three must pass. Visibility with no appeal path is notification.
An appeal to someone who cannot reverse the decision is theater.

## The Override Integrity Test

If you tell Claude a human reviews the decisions, expect four tests:

| Test | Decorative | Real |
|---|---|---|
| Time | No review time before it executes | Review time in the flow |
| Volume | More decisions than a human could review | Volume matched to capacity |
| Cost | Overriding is penalized or flagged | Overriding is normal and free |
| Default | Acceptance is automatic | Both paths need equal action |

Fail any one and the override records as absent, not present. This is the
finding builders resist most, which is why the skill re-runs it before
closing.

## Reading the Findings

Each finding carries lane, mechanism, affected population, severity, and
remedy.

| Severity | Meaning |
|---|---|
| Critical | Affects pay or continued work with no contestability |
| High | Affects opportunity or standing, weak contestability |
| Moderate | Meaningful asymmetry or a live gaming path |
| Low | Design concern, no current harm path |

Findings do not average. A Critical does not get offset by clean lanes
elsewhere.

## Best Time To Run It

Before the system ships. At design time the remedies cost design hours; at
deployment they cost trust you cannot buy back. Design-time runs add three
requirements: contestability built before the decision mechanism, every
metric shipped with its gaming path documented, and every anticipated gray
area given a named escalation route or a recorded decision to accept the
risk.

## The Core Question

Every lane in this audit descends from one question: if a human manager did
what this system does, in the open, would it be acceptable? Encoding a
management decision does not launder it.

## Pairs Well With

- `motivation-architecture` for what the control system does to motivation
  quality
- `human-in-loop-escalation` for building the escalation paths this audit
  demands
- `accountability-chain` for who owns the algorithm's decisions
- `de-skilling-guard` for what automated direction does to worker
  capability over time

## Attribution

Built and documented by YourVisionYourCreation LLC.
Theoretical foundation: Kellogg, Valentine, and Christin (2020),
*Academy of Management Annals*.
yourvisionyourcreation.com

---

*Licensed under CC BY 4.0*
