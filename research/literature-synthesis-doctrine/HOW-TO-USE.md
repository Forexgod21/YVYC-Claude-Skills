# How To Use: literature-synthesis-doctrine

**Category:** research
**Author:** YourVisionYourCreation LLC
**License:** CC BY 4.0

---

## What This Skill Does

Converts a pile of sources into an argument about the state of
knowledge. Organization by theme instead of by source, a
source-by-theme matrix built before any prose, tight claim-source
binding, a hard citation guard (unverifiable means deleted), source
tiering, analysis of disagreement, and a gap statement precise enough
to design a study against.

## The Problem It Solves

Two failures, one common and one fatal. The common one: the book
report, one paragraph per source in reading order, which every
reviewer from course grader to journal referee detects in one page
and marks down accordingly. The fatal one: fabricated references,
plausible-looking citations of sources that do not exist or do not
say what they are cited for, which are now cheap to produce and
which destroy an author's credibility retroactively when found.

## When It Activates

- Writing or revising a literature review, background section,
  related-work section, annotated bibliography, or evidence summary
- Organizing multiple sources into a single argument
- Generating, checking, or formatting citations
- Deriving a research gap or research question from existing work
- Any academic or professional task where sources carry the argument

## Installation

1. Create a folder named `literature-synthesis-doctrine` in your
   Claude skills location.
2. Place `SKILL.md` inside it.
3. Pair it with `scholar-practitioner` (the full academic writing
   standard) or `scholar-practitioner-tempo` (the program-calibrated
   edition with APA 7 mechanics). Citation format lives there;
   citation integrity lives here.

## Example Invocations

> "Write my literature review from these twelve sources."

The matrix comes first: sources by themes, findings in cells. Sources
filling no cell are named and dropped; one-source themes are demoted;
conflict columns become sections. Then the prose, written from the
matrix, ending at a gap the corpus actually supports.

> "Find me sources that support my argument."

Reframed on the spot: a corpus assembled to agree is confirmation
harvesting, and its reviews collapse at first hostile read. The
search includes the disconfirming work, and the argument gets built
from what the whole field says.

> "Add citations to this."

The guard, applied per citation: verified to exist and to contain the
claimed content, or not added. A remembered-but-unconfirmed source is
flagged as unconfirmed, never dressed in confident APA.

> "What's the research gap here?"

The gap derived from the matrix and checked against it, stated
narrowly enough that a study could be designed against it, with any
study that already fills the candidate gap surfaced rather than
ignored.

## What Changes In Claude's Behavior

| Without This Skill | With This Skill |
|---|---|
| One paragraph per source, in reading order | Sections named for themes, sources conversing inside them |
| Prose written straight from reading notes | The matrix built first; prose written from the matrix |
| "Studies show..." with no study attached | Every aggregate claim names its specific studies |
| Plausible citations shipped on format alone | Every citation verified to exist and say the thing, or deleted |
| A blog post and a meta-analysis weighted equally | Tier stated wherever a claim bears load |
| Conflicts between sources papered over | Divergence analyzed: populations, measures, definitions, eras |
| Gaps declared by not looking | Gaps checked against the corpus before they justify anything |

## What This Skill Will Refuse

- Shipping a citation that could not be verified
- Repairing an unverifiable reference into plausibility instead of
  deleting it
- Citing a study known only through another author's summary as if
  read directly
- Building a corpus that excludes disconfirming work
- Declaring a gap the assembled literature has already filled
- Letting the argument travel further than the cells support without
  labeling the excess as the author's own inference

## How It Works With Other Skills

| Pairing | Division of labor |
|---|---|
| `scholar-practitioner` | Owns the academic writing standard for the full document. This doctrine owns the synthesis machinery inside the review. |
| `scholar-practitioner-tempo` | Owns APA 7 mechanics and program calibration. Format there, integrity here. |
| `adversarial-verification-doctrine` | Owns general claim verification. The citation guard is its zero-tolerance application to references. |
| `commit-or-concede` | Owns the truth floor. An unconfirmed source is a concession, stated as one. |
| `human-signal` | Strips AI patterning from the review's prose once the synthesis is sound. |

---

*YourVisionYourCreation LLC, yourvisionyourcreation.com*
*Licensed under CC BY 4.0*
