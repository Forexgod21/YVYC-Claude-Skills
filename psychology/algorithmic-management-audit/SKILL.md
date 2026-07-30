---
name: algorithmic-management-audit
version: 1.0
author: YourVisionYourCreation LLC
license: CC BY 4.0
category: psychology
description: >
  Activate when evaluating, designing, or repairing any system where
  software directs, evaluates, or disciplines human work: gig
  platforms, AI-assisted management tools, productivity monitoring,
  automated scheduling, algorithmic performance scoring, or agentic
  systems that assign tasks to people. Audits the system across the
  six control functions of algorithmic management and scores its
  human cost against its control benefit.
---

# Algorithmic Management Audit

## Attribution

Built and documented by YourVisionYourCreation LLC (YVYC).

Theoretical foundation: Kellogg, K. C., Valentine, M. A., and Christin, A.
(2020), "Algorithms at Work: The New Contested Terrain of Control,"
*Academy of Management Annals*, which maps the control functions this
audit operationalizes.

Attribution: YourVisionYourCreation LLC, yourvisionyourcreation.com

## Doctrine Statement

When software manages people, management decisions do not disappear. They
get encoded, scaled, and hidden. An algorithm that assigns shifts, scores
performance, or nudges behavior is a manager whose reasoning nobody can
question in the hallway.

The audit exists because encoding a management decision does not launder
it. It removes the one thing that made the decision survivable: a human
who could be asked why.

## The Universal So-What

Systems that direct human work get built by teams who describe them in
technical language, which means the management functions inside them never
get reviewed as management. A scoring model gets a model review. It does
not get the review a supervisor would get. This audit applies the second
review to systems that only ever received the first.

## Theory as Mechanism

The six control functions are load-bearing. Their specific value is that
they identify what a system *does* regardless of what it is *called*. A
feature named "smart routing" that concentrates opportunity toward high
scorers is performing the reward and restriction functions whether or not
anyone involved described it that way. The framework defeats euphemism,
which is the primary obstacle to auditing these systems honestly.

## The Six Control Functions

Every system is inventoried against all six. Functions are identified by
behavior, never by the name the builder gave the feature.

| Function | What it does | Where it hides |
|---|---|---|
| Restricting | Limits what options a worker can see or take | Defaults, filtered views, unavailable choices |
| Recommending | Steers choices without formally requiring them | Nudges, suggested actions, ordering |
| Recording | Captures worker activity as data | Telemetry, activity logs, screen time |
| Rating | Scores the worker | Quality scores, rankings, tiers |
| Replacing | Substitutes automated judgment for human judgment | Auto-decisions, thresholds, gates |
| Rewarding | Distributes pay, access, or opportunity by output of the above | Routing, bonuses, tier privileges |

The compounding case is the one to watch: rating plus rewarding in a
single mechanism creates a loop where yesterday's score determines
tomorrow's opportunity, which determines tomorrow's score. Nobody designs
that loop deliberately. It assembles itself from two reasonable features.

## The Six Audit Lanes

**Lane 1: Function inventory.** Which of the six functions does the system
actually exercise, regardless of feature naming? Every identified function
is named with the specific mechanism performing it.

**Lane 2: Asymmetry inventory.** What does the system know about the
worker that the worker does not know about the system? Information
asymmetry is the resource algorithmic control runs on, and it is measured
here rather than assumed.

**Lane 3: Transparency and contestability testing.** For every decision
affecting pay, scheduling, or standing, three separate questions:

- Can the worker *see* that the decision was made?
- Can the worker *understand* the basis for it?
- Can the worker *contest* it to someone with authority to reverse it?

All three must pass. Visibility without an appeal path is notification,
not contestability. An appeal path to someone who cannot reverse the
decision is theater.

**Lane 4: Gaming scan.** For every metric, state the behavior that
maximizes the metric without serving the actual goal. This is not a
prediction of bad actors; it is a specification of what the metric
rewards. Any metric with a gaming path shorter than the honest path will
be gamed, and that is a design finding, not a worker finding.

**Lane 5: Override integrity.** Where a human override exists, test
whether it is real:

| Test | Decorative override | Real override |
|---|---|---|
| Time | No time to review before it executes | Review time built into the flow |
| Volume | More decisions than any human could review | Volume matched to review capacity |
| Cost | Overriding is penalized or logged as an exception | Overriding is a normal, cost-free action |
| Default | Override requires action; acceptance is automatic | Both paths require equal action |

An override that fails any of these four is decorative and gets recorded
as absent, not as present.

**Lane 6: JumpMaster check.** Which gray-area judgment calls is the system
resolving silently at scale that should escalate to a human? Every gray
area an algorithm resolves quietly is a decision nobody made, applied to
thousands of people. This lane names them and requires an escalation path
for each.

## Findings Format

Each finding carries a lane, the mechanism, the affected population, a
severity, and a remedy.

| Severity | Meaning |
|---|---|
| Critical | Affects pay or continued work with no contestability |
| High | Affects opportunity or standing with weak contestability |
| Moderate | Meaningful asymmetry or a live gaming path |
| Low | Design concern with no current harm path |

Findings are not averaged into an overall score. A Critical finding is not
offset by clean lanes elsewhere.

## Design-Time Application

The audit runs best before a system ships, where remedies cost design time
rather than trust. At design time three additional requirements attach:

- The contestability path is built before the decision mechanism, not
  after.
- Every metric ships with its gaming path documented.
- Every gray area the system will encounter has a named escalation route
  or an explicit decision to accept the risk, recorded.

## When the Manager Is an Agent

The moment an agentic system assigns, evaluates, or prioritizes human
work, it is performing management and this audit applies to it. This
includes agents assigning tasks to human reviewers, agents triaging work
queues, and agents scoring human output. The JumpMaster check carries
extra weight here: an agent resolving gray areas alone at machine speed
produces more unreviewed management decisions per hour than any human
supervisor could.

## Adversarial Evaluator Gate

Before any audit ships:

> If a hostile reviewer wanted to prove this audit was captured by the
> people who built the system, which lane would they say was run softly?

The answer is usually Lane 5, because override integrity is the finding
builders most resist. That lane gets re-run against the four tests
explicitly before the audit closes.

## The Core Question

Every lane descends from one question: if a human manager did what this
system does, in the open, would it be acceptable? Encoding a management
decision does not launder it.

## What This Skill Will Refuse

- Accepting feature names in place of function analysis
- Scoring an override as present when it fails the integrity tests
- Averaging a Critical finding away against clean lanes
- Treating a gaming path as a worker integrity problem
- Auditing only the technical system while excluding its management
  functions

## Pairs Well With

- `motivation-architecture` for what the control system does to motivation
  quality
- `human-in-loop-escalation` for building the escalation paths this audit
  demands
- `accountability-chain` for who owns the algorithm's decisions
- `de-skilling-guard` for what automated direction does to worker
  capability over time

---

*YourVisionYourCreation LLC, yourvisionyourcreation.com*
*Licensed under CC BY 4.0*
