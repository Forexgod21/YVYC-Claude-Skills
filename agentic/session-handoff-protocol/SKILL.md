---
name: session-handoff-protocol
version: 1.0
author: YourVisionYourCreation LLC
license: CC BY 4.0
category: agentic
description: >
  Eliminates the cold-start tax between sessions via a continuity capsule:
  mission line, decision ledger, open loops, dead ends, convention deltas,
  state facts, and next-actions queue. Trigger at the end of any substantive
  session, before context compaction, after major decisions, at the start of
  any session where a capsule exists, and whenever the operator re-explains
  settled ground. Cross-session state only; within-session compaction
  belongs to compaction-integrity-protocol.
---

# Session Handoff Protocol

**Attribution:** YourVisionYourCreation LLC, yourvisionyourcreation.com
**Doctrine class:** YVYC library, agentic category

---

## Universal So-What

Sessions end. Context windows fill, get compacted, or close entirely,
and everything the agent held in working state evaporates with them.
The doctrine library governs how an agent behaves while a session is
alive. Nothing governs what survives when it dies. The result is a tax
the operator pays at the top of every session: re-stating the mission,
re-issuing settled decisions, watching the agent rediscover a path that
was ruled out three sessions ago.

The handoff capsule is the fix. State is written at the moment it is
cheapest to write, while it is still loaded, and read at the moment it
is most valuable, before the first output of the next session. The test
of a good handoff: the resumed session's first response reads like the
same operator's agent continuing the same mission, not a stranger doing
intake.

---

## The Capsule

One artifact per project. One screen of text. Seven sections, every
line load-bearing. It lives in the repository as a plain file the
operator can read, diff, and version (for example `CAPSULE.md` at the
project root, or wherever the operator's doctrine room assigns it).

| Section | Carries |
|---|---|
| **Mission line** | One sentence. What this project is driving toward. Unchanged most sessions; when it changes, that change is the headline. |
| **Decision ledger** | Decisions made, each with the reason it was made. The reason is what prevents re-litigation: a bare decision invites a fresh debate, a reasoned one closes it. |
| **Open loops** | Work in flight, each with its exact state: what is done, what is not, and where the seam is. "Auth flow: token issue works, refresh untested" beats "working on auth." |
| **Dead ends** | Approaches tried and invalidated, with the evidence that killed them. This section pays for the whole capsule: unrecorded dead ends get re-explored at full cost. |
| **Convention deltas** | Standing rules established since the last capsule. This section is a staging area, not a home: deltas migrate into the operator's doctrine files (CLAUDE.md, class rules) and are then removed here. |
| **State facts** | Environment facts that outlive the session and are not discoverable in seconds: which branch carries what, which service is stubbed, which credential the operator holds offline. |
| **Next actions** | An ordered queue. The first item must be startable with zero clarifying questions; if it is not, the blocker is named beside it. |

---

## Write Discipline

**When the capsule is written:**

1. At the end of any substantive session, as the final act before the
   turn closes.
2. Before any context compaction, so the capsule is authored from full
   context rather than from a summary of a summary.
3. Immediately after any major decision, pivot, or invalidation, even
   mid-session. A capsule that only updates at session end loses the
   sessions that end unexpectedly.

**How it is written:**

- **Overwrite, never append.** The capsule is a ledger of current
  state, not a log of history. Version control is the archive; the
  capsule is the present tense.
- **Ceiling, not floor.** One screen. When the capsule outgrows a
  screen, the excess is either doctrine (migrate it), history (delete
  it, git holds it), or bloat (cut it).
- **Anchored, not timestamped trust.** The capsule states what it was
  written against: a commit hash, a milestone, a named artifact
  version. "Current as of commit a9cf891" is verifiable; "current as
  of Tuesday" is not.
- **No secrets. Ever.** The capsule is a committed, readable file.
  Credentials, tokens, and private personal detail never enter it.
  State facts may say a credential exists and who holds it, never what
  it is.

---

## Load Discipline

**First action of a resumed session:** read the capsule. **Second
action:** verify it against reality before trusting it. Files change
between sessions. Branches merge. Other agents and other humans do
work. The trust order is fixed:

> **Current reality → capsule → model memory.**

Verification is proportional, not exhaustive: check the anchor (does
the stated commit match, does the named branch exist, is the stubbed
service still stubbed), then proceed. When the capsule contradicts
reality, reality wins, the capsule is corrected on the spot, and the
discrepancy is surfaced to the operator in one line. A capsule that
fails verification is demoted to a hypothesis, never silently obeyed.

Loading is not optional when a capsule exists. "I remember this
project" is model memory claiming rank it does not hold.

---

## What the Capsule Is Not

1. **Not a chat log or session summary.** Narrative of what happened
   is history; the capsule carries only what the next session needs to
   act.
2. **Not hidden memory.** It is an operator-visible, operator-editable
   file with full provenance. For the defense doctrine on persistent
   stores the operator cannot see, this skill defers entirely to
   `memory-poisoning-defense`.
3. **Not a doctrine fork.** Rules do not live here. Convention deltas
   pass through on their way to the canon (`correction-conversion-protocol`,
   the operator's doctrine room) and are deleted once they land. A
   capsule that accumulates rules has become a second canon, and two
   canons diverge.
4. **Not an apology archive.** Misses convert to rules and move on. The
   capsule records the rule's destination, never the contrition.

---

## Failure Modes

| Failure | Correction |
|---|---|
| **Capsule bloat.** The file grows past a screen and stops being read. | Enforce the ceiling at write time. Migrate doctrine out, delete history, cut the rest. |
| **Stale authority.** A capsule written five sessions ago is loaded and trusted over the current repository. | Verify-on-load is mandatory. The anchor makes staleness detectable; reality always outranks the file. |
| **Write skipped on a "small" session.** The session that ruled out an approach in two turns leaves no record, and the approach returns. | Any session that decided or invalidated anything updates the capsule. Size of session does not gate the write. |
| **Load skipped on confidence.** The agent proceeds on model memory because the project feels familiar. | Model memory holds rank zero. A capsule that exists is read, every time. |
| **Rules nesting in the capsule.** Convention deltas stop migrating and the capsule forks the canon. | Deltas are staged, migrated, and deleted. A delta present across two consecutive capsules is a migration failure to fix now. |
| **Secrets leaking in.** A token lands in a committed file. | Hard ban, checked at write time. Reference the credential's existence and holder, never its value. |

---

## Boundary (Read Before Applying)

| Skill | Governs |
|---|---|
| `compaction-integrity-protocol` | State surviving compaction *within* a live session. |
| `correction-conversion-protocol` | Corrections becoming standing class rules. The capsule stages deltas for it, nothing more. |
| `doctrine-room-architecture` | The canon itself: rule lifecycle, decision governance across projects. |
| `memory-poisoning-defense` | Persistent stores the operator cannot inspect. The capsule avoids that class by design. |
| `session-handoff-protocol` | Cross-session mission state: what is written when context dies, and how it is loaded and verified when work resumes. |

Overlap is a defect. State lives here; rules live in the canon; hidden
memory is a different threat surface entirely.

---

## Compliance Check (Run at Session Close and Session Open)

1. Does a capsule exist, and was it loaded before the first output?
2. Was the capsule verified against its anchor before being trusted?
3. Does every decision in the ledger carry its reason?
4. Is every dead end recorded with the evidence that killed it?
5. Is the first next-action startable without a clarifying question?
6. Have convention deltas migrated to the canon and been cleared?
7. Is the capsule still one screen, and is its anchor current?

---

## Adversarial Evaluator Gate

**What would a hostile evaluator attack first?**

The capsule becoming a stale authority. A confidently loaded wrong
state is worse than a cold start: the cold-start agent asks, the
poisoned agent acts. The defense is structural, not aspirational:
verify-on-load is a mandatory step with a concrete anchor to check,
and the trust order places reality above the file without exception.

The second attack: the capsule quietly becoming a second doctrine
system. Every rule that nests in the capsule instead of migrating is a
fork of the canon, and forks diverge silently until they conflict
loudly. The staging-area design, the two-capsule migration deadline,
and the one-screen ceiling exist to make that accumulation impossible
to sustain.

---

*YourVisionYourCreation LLC, yourvisionyourcreation.com*
*Licensed under CC BY 4.0*
