# Human Signal — How To Use

**Skill:** `human-signal`
**Author:** YourVisionYourCreation LLC
**Version:** 1.0
**License:** CC BY 4.0

---

## What This Skill Does

Human Signal detects and removes AI writing patterns — the vocabulary,
structural habits, and communication tics that make text read as
machine-generated. It operates in two modes: full rewrite or scan-only.
The goal is not cleaner text. The goal is authentic voice — writing that
carries a human signal a reader trusts.

---

## Quick Start

Paste your text and use any of these triggers:

```
Remove the AI patterns from this.
```
```
De-AI this post before I publish it.
```
```
Strip the robot out of this.
```
```
Make this sound like a person wrote it.
```
```
Scan this for AI tells. [scan mode — no rewrite]
```
```
Flag only. Don't rewrite. [scan mode]
```

---

## Modes

### Rewrite Mode (default)

Full detection and correction. Returns four sections:

1. **Patterns detected** — every AI pattern found, quoted exactly
2. **Rewritten version** — clean prose, all patterns resolved
3. **What changed** — summary of the major edits
4. **Second-pass audit** — catches anything that survived the first pass

Use for: blog posts, LinkedIn content, investor emails, proposals, any
content going to a real audience.

### Scan Mode

Detection only. No changes made. Returns two sections:

1. **Patterns detected** — grouped by severity
2. **Assessment** — clear problem vs. judgment call for each flag

Use for:
- Content you want to evaluate before editing yourself
- Other people's writing you shouldn't alter
- A fast audit before a full edit session

---

## Context Profiles

Pass a profile to calibrate how strict the audit runs:

| Profile | Use When |
|---|---|
| `linkedin` | Short-form social posts |
| `blog` | Default. Long-form prose. |
| `technical` | Writing with code, APIs, or architecture content |
| `investor` | Investor emails, fundraising decks, pitch content |
| `docs` | Documentation, READMEs, user guides |
| `casual` | Internal notes, Slack messages, quick drafts |

**Example:**
```
Rewrite this as a linkedin post. Remove all AI patterns.
```
```
Audit this investor email. Scan only — flag everything.
```

If you don't specify a profile, the skill auto-detects from content signals.
Short text with hashtags → LinkedIn. Code blocks → Technical. Salutation
with funding language → Investor. Default: Blog.

---

## Severity Levels

### Critical — Fix immediately
- Chatbot artifacts ("I hope this helps!", "Great question!")
- Knowledge cutoff disclaimers leaking into published prose
- Vague attributions without named sources
- Significance inflation on routine events

### Primary — Fix before publishing
- Tier 1 vocabulary (delve, robust, leverage, pivotal, seamless...)
- Template phrase slot-fills
- "Let's" openers used as transitions
- Formulaic openings ("In the rapidly evolving world of...")
- Bold overuse
- Em dash frequency above one per 1,000 words
- Sycophantic validation ("Great question!")

### Polish — Fix when time allows
- Generic conclusions ("The future looks bright")
- Uniform paragraph length
- Transition padding (Moreover, Furthermore, Additionally)
- Parenthetical hedging

---

## Vocabulary Detection — Three Tiers

The skill uses a tiered vocabulary detection system:

**Tier 1** — Always flag. These words are high-signal AI indicators regardless
of context. Replace on sight.

**Tier 2** — Flag in clusters. Legitimate individually. Two or more in the same
paragraph signals AI-generated prose.

**Tier 3** — Flag at high density. Common words AI over-uses to pad vague
claims. Flag only when they saturate the text.

See SKILL.md for the full replacement tables.

---

## When To Recommend Full Reconstruction

If the text shows all three of the following conditions, patching phrases
will not fix it. The structure itself is AI-generated.

- Five or more Tier 1 vocabulary hits
- Three or more distinct pattern categories triggered
- Uniform sentence and paragraph length throughout

In this case, recommend: state the core point in one sentence and rebuild
from there.

---

## What This Skill Does Not Do

- It does not change meaning, technical detail, or factual content.
- It does not apply rules mechanically when context makes a pattern acceptable.
- It does not over-edit writing that is already strong.
- It does not sand away personality in pursuit of AI avoidance — over-polishing
  can push human writing *toward* AI statistical profiles.

The replacement tables are defaults, not mandates. If a flagged word is the
genuinely right choice in context, the skill will preserve it and say why.

---

## Installation

Add `human-signal` to your Claude skill library and reference it in your
project or session context. Works with claude.ai Projects and Claude Code.

For direct use without installation, paste the SKILL.md contents into your
Claude Project instructions or at the start of a session.

---

## Example Prompts

**Full rewrite, default profile:**
```
Remove all AI patterns from this blog post. [paste text]
```

**Scan only, investor profile:**
```
Scan this investor email for AI tells. Don't rewrite anything. [paste text]
```

**Rewrite, LinkedIn profile:**
```
Rewrite this as LinkedIn content. Strip all AI patterns. [paste text]
```

**Fast pass:**
```
Quick audit — Critical and Primary patterns only. Rewrite what you find. [paste text]
```

**Full reconstruction signal:**
```
This reads completely AI-generated. Assess it and tell me if I need to
rebuild from scratch or if a patch will work. [paste text]
```

---

*YourVisionYourCreation LLC — yourvisionyourcreation.com*
*Licensed under CC BY 4.0*
