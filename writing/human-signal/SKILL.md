---
name: human-signal
version: 1.0
author: YourVisionYourCreation LLC
license: CC BY 4.0
category: writing
description: >
  Audit and rewrite content to remove AI writing patterns and restore
  authentic human voice. Activate when asked to "remove AI patterns,"
  "clean up AI writing," "make this sound human," "audit for AI tells,"
  "de-AI this," or "strip the robot out of this." Supports a scan-only
  mode that flags patterns without rewriting. Applies context profiles
  to adjust rule strictness by format and audience.
---

# Human Signal — AI Pattern Detection & Voice Restoration

## Doctrine

Every piece of writing either carries a human signal or it doesn't.
AI patterns are noise — they degrade signal, flatten voice, and mark
the writer as a machine to any trained reader. This skill's mission is
to detect that noise, eliminate it, and restore the signal.

Writing should demonstrate confidence — not assert it. It should show
specificity — not claim it. It should earn authority — not announce it.

---

## Operating Modes

**`rewrite`** (default) — Detect patterns, eliminate them, return clean prose.

**`scan`** — Detect and flag only. No rewriting. Use when:
- The writer wants to evaluate patterns before deciding what to fix
- Patterns may be intentional — AI tells are not always wrong in context
- Content belongs to someone else and should not be altered
- You need a fast pass before a full edit session

Trigger `scan` mode when the user says: "scan," "flag only," "audit only,"
"just show me what's wrong," "detect only," "what patterns are here," or similar.
Default to `rewrite` if not specified.

---

## Rewrite Mode — Execution Protocol

1. **Detect** — Identify every pattern present, citing the exact offending text
2. **Rewrite** — Return clean prose with all patterns resolved
3. **Account** — Summarize what changed and why
4. **Second Pass** — Re-read the rewrite. Catch anything that survived. Fix it inline.
   If the rewrite is clean, confirm it.

## Scan Mode — Execution Protocol

1. **Detect** — Identify every pattern present, cited exactly
2. **Assess** — For each flag, state whether it is a clear problem or a judgment call.
   Some patterns are legitimate in context. Call the difference.

---

## Pattern Library

### Section 1 — Formatting Patterns

**Em dashes** — Replace with commas, periods, parentheses, or restructure as
two sentences. Target: zero. Hard ceiling: one per 1,000 words. This applies
to headings as well as body prose. Catch both the Unicode em dash (—) and the
double-hyphen substitute (--).

**Bold overuse** — Strip bold from most phrases. One bolded item per major
section at most, and only when restructuring the sentence to lead with the
point would not work better.

**Emoji in headers** — Remove entirely. Social posts may carry one or two emoji
sparingly, at the end of a line, never mid-sentence. Everywhere else: none.

**Bullet saturation** — Convert bullet-heavy sections into prose. Bullets are
for genuinely list-like content: feature comparisons, sequential steps, parameter
reference. If bullets are carrying narrative, they are wrong.

**Inline-header bullets** — Lists where each item opens with a bold header that
restates itself ("**Performance:** Performance improved...") are AI scaffolding.
Strip the bold header. Write the point as a sentence. If headers are necessary,
they belong as section headings, not list prefixes.

**Header overuse** — More than three subheadings in under 300 words signals AI
trying to look organized. Merge sections or use prose transitions.

**Title case saturation** — Sentence case for subheadings always. Title case
only for the primary title, if at all.

---

### Section 2 — Vocabulary Patterns

Words are organized into three detection tiers based on signal strength.

**Tier 1 — Always flag.** These words appear at disproportionate rates in
AI-generated text regardless of context. Replace on sight.

| Replace | With |
|---|---|
| delve / delve into | explore, dig into, examine |
| landscape (metaphor) | field, industry, space, market |
| tapestry | describe the actual complexity |
| realm | area, field, domain |
| paradigm | model, approach, framework |
| embark | start, begin |
| beacon | rewrite entirely |
| testament to | shows, proves, demonstrates |
| robust | strong, reliable, solid |
| comprehensive | thorough, complete, full |
| cutting-edge | latest, newest, advanced |
| leverage (verb) | use |
| pivotal | important, key, critical |
| underscores | highlights, shows, makes clear |
| meticulous / meticulously | careful, detailed, precise |
| seamless / seamlessly | smooth, easy, without friction |
| game-changer / game-changing | describe what specifically changed |
| utilize | use |
| watershed moment | turning point, shift |
| nestled | is located, sits |
| vibrant | describe what makes it active, or cut |
| thriving | growing, active — or cite a number |
| showcasing | showing, demonstrating — or cut the clause |
| deep dive / dive into | examine, look at, explore |
| unpack / unpacking | explain, break down, walk through |
| bustling | busy, active — or name what makes it so |
| intricate / intricacies | complex, detailed — or name the complexity |
| ever-evolving | changing, growing — or describe how |
| enduring | lasting, long-running — or cite how long |
| daunting | hard, difficult, challenging |
| holistic / holistically | complete, full — or describe what is included |
| actionable | practical, useful, concrete |
| impactful | effective, significant — or describe the impact |
| learnings | lessons, findings, takeaways |
| thought leader / thought leadership | expert, authority — or describe the contribution |
| best practices | what works, proven approach, standard method |
| at its core | cut — state the thing directly |
| synergy / synergies | describe the actual combined effect |
| interplay | relationship, connection, interaction |
| in order to | to |
| due to the fact that | because |
| serves as | is |
| features (verb) | has, includes |
| boasts | has |
| commence | start, begin |
| ascertain | find out, determine, learn |
| endeavor | effort, attempt, try |
| keen (as intensifier) | interested, eager — or cut |
| embrace (metaphor) | adopt, accept, use, switch to |
| the future looks bright | cut — say something specific |
| only time will tell | cut — say something specific |
| marking a pivotal moment | state what happened |
| despite challenges… continues to thrive | name the challenge and the response, or cut |

**Tier 2 — Flag when two or more appear in the same paragraph.** These words
are legitimate individually. Clustering signals AI-generated prose.

| Replace | With |
|---|---|
| harness | use, take advantage of |
| navigate / navigating | work through, handle, deal with |
| foster | encourage, support, build |
| elevate | improve, raise, strengthen |
| unleash | release, enable, unlock |
| streamline | simplify, speed up |
| empower | enable, let, allow |
| bolster | support, strengthen |
| spearhead | lead, drive, run |
| resonate / resonates with | connect with, appeal to, matter to |
| revolutionize | change, transform — or describe what changed |
| facilitate / facilitates | enable, help, allow |
| underpin | support, form the basis of |
| nuanced | specific, subtle — or name the actual nuance |
| crucial | important, key, necessary |
| multifaceted | describe the actual facets, or cut |
| ecosystem (metaphor) | system, community, network, market |
| myriad | many, numerous — or give a number |
| plethora | many, a lot — or give a number |
| encompass | include, cover, span |
| catalyze | start, trigger, accelerate |
| reimagine | rethink, redesign, rebuild |
| galvanize | motivate, rally, push |
| augment | add to, expand, supplement |
| cultivate | build, develop, grow |
| illuminate | clarify, explain, show |
| elucidate | explain, clarify, spell out |
| transformative / transformation | describe what changed and how |
| cornerstone | foundation, basis, key part |
| paramount | most important, top priority |
| poised (to) | ready, set, about to |
| burgeoning | growing, emerging — or cite a number |
| nascent | new, early-stage, emerging |
| quintessential | typical, classic, defining |
| overarching | main, central, broad |
| underpinning / underpinnings | basis, foundation, what supports it |
| paradigm-shifting | describe what actually shifted |

**Tier 3 — Flag at high density only.** Common words AI saturates text with
to pad vague claims. Flag when they appear at noticeable frequency — roughly
3% or more of total word count.

| Word | Fix |
|---|---|
| significant / significantly | Replace with specifics: numbers, comparisons, examples |
| innovative / innovation | Describe what is actually new |
| effective / effectively | Say how, or cite a metric |
| dynamic / dynamics | Name the actual forces or changes |
| compelling | Say why it compels |
| unprecedented | Name the precedent it breaks, or cut |
| exceptional / exceptionally | Cite what makes it an exception |
| remarkable / remarkably | Say what is worth remarking on |
| sophisticated | Describe the sophistication |
| instrumental | Say what role it played |
| world-class / state-of-the-art / best-in-class | Cite a benchmark or comparison |

---

### Section 3 — Sentence and Structural Patterns

**Hollow intensifiers** — Cut `genuine`, `real` (as in "a real improvement"),
`truly`, `quite frankly`, `to be honest`, `let's be clear`, `it is worth noting
that`. State the fact without the frame.

**Vague endorsement** — Cut or replace `worth reading`, `worth paying attention
to`, `worth a look`, `worth exploring`, `worth your time`. These substitute a
generic thumbs-up for a specific reason. Say why something matters instead.

**Hedging language** — Cut `perhaps`, `could potentially`, `it is important to
note that`, `to be clear`. Make the point directly.

**The X-not-Y construction** — "It's not X — it's Y." Maximum one per piece,
only when it serves the argument. Rewrite as a direct positive statement.

**Compulsive rule of three** — Vary groupings. Use two items, four items, or a
full sentence. Maximum one "adjective, adjective, and adjective" pattern per
piece.

**Missing connective tissue** — Each paragraph must connect to the previous
one. If paragraphs can be rearranged without the reader noticing, the transitions
are missing.

**Uniform sentence length** — Mix short punchy sentences (3–8 words) with
longer ones (20+). If most sentences fall in the 15–25 word range, the text
sounds metronomic. Fragments work. Questions break the rhythm.

**Uniform paragraph length** — If every paragraph is 3–5 sentences and roughly
the same size, vary deliberately. Some paragraphs should be one sentence.

**Formulaic opening** — If the piece opens with broad context before reaching
the point ("In the rapidly evolving world of..."), rewrite. Lead with the news
or the insight. Context comes second.

**Copula avoidance** — AI substitutes fancier verbs for "is" and "has":
"serves as," "features," "boasts," "presents," "represents." These read like
press releases. Default to "is" or "has" unless a specific verb adds real
meaning.

**Synonym cycling** — AI rotates synonyms to avoid repetition:
"developers… engineers… practitioners… builders." Human writers repeat the
clearest word. If the right word appears three times in a paragraph, keep all
three. Forced variation reads as thesaurus abuse.

---

### Section 4 — Communication Patterns

**Chatbot artifacts** — "I hope this helps!", "Certainly!", "Absolutely!",
"Great question!", "Feel free to reach out," "Let me know if you need anything
else," "In this article, we will explore…," "Let's dive in!" These are
conversational tics from chat interfaces. Remove entirely.

**"Let's" openers** — "Let's explore," "Let's take a look," "Let's break this
down," "Let's examine." AI uses these as false-collaborative openers to delay
the actual point. Just start with the point.

**Sycophantic validation** — "Great question!", "Excellent point!", "You're
absolutely right!", "That's a really insightful observation." Remove entirely.

**Acknowledgment loops** — "You're asking about," "The question of whether,"
"To answer your question," "That's a great question. The..." — restating the
prompt before answering is filler. The reader knows what they asked. Answer.

**Transition padding** — "Moreover," "Furthermore," "Additionally" — restructure
so the connection is obvious, or use "and," "also," "on top of that."
"In today's [X]," "In an era where" — cut or state specific context.
"In conclusion," "In summary," "To summarize" — a strong conclusion is
self-evident.

**Reader-steering frames** — "Here's what's interesting," "Here's what caught
my eye," "Here's what stood out," "What surprised me most," "I was fascinated
to discover." If the content is genuinely interesting, the writing should earn
that — not announce it. Cut the frame and present the thing.

**Confidence calibration stacking** — "Notably," "Importantly," "Significantly,"
"Certainly," "Undoubtedly" — one per 2,000 words is acceptable. Three in 500
words is AI emphasis stacking. Flag by density.

**Rhetorical question stalling** — "But what does this mean?" "So why should
you care?" "What's next?" — if you know the answer, say it. Rhetorical
questions must be earned by strong setup, not dropped as transitions.

**Parenthetical hedging** — "(and, increasingly, Z)" / "(or, more precisely, Y)"
/ "(and perhaps more importantly, W)" — AI inserts these to sound nuanced without
committing. If the aside matters, give it its own sentence. Otherwise, cut.

---

### Section 5 — Credibility and Attribution Patterns

**Vague attributions** — "Experts believe," "Studies show," "Research suggests,"
"Industry leaders agree" without naming the source. Either cite a specific
source or drop the attribution and state the claim directly.

**Significance inflation** — "Marking a pivotal moment in the evolution of..."
"A watershed moment for the industry" — these inflate routine events into
history-making ones. State what happened and let the reader judge.

**Novelty inflation** — "He introduced a term," "She coined the phrase," "a
concept nobody's naming," "a failure mode nobody talks about." Most ideas in a
conversation are applications of existing concepts, not inventions. Claiming
novelty without basis is factually risky and reads as promotional. Describe
what the person *did with* the concept, not that they discovered it.
Related patterns: "the failure mode nobody's naming," "a problem nobody talks
about," "what nobody tells you about," "the insight everyone's missing."

**Notability stacking** — "cited in The New York Times, BBC, Financial Times,
and The Hindu." If a source matters, use it with context. One specific
reference beats four name-drops.

**False concession** — "While X is impressive, Y remains a challenge." Both
halves are vague. This sounds balanced without weighing anything. Name what is
impressive. Name the actual challenge. Or pick a position and argue it.

**False range** — "from the Big Bang to dark matter," "from ancient civilizations
to modern startups." These sound sweeping but say nothing. List the actual
topics or name the one that matters.

**Promotional language** — "nestled within the breathtaking foothills," "a
vibrant hub of innovation," "a thriving ecosystem." Replace with plain
description. If it reads like a brochure, rewrite it as a fact.

**Formulaic challenges** — "Despite challenges, [subject] continues to thrive."
"While facing headwinds, the organization remains resilient." Name the actual
challenge and the actual response, or cut.

**Cutoff disclaimers** — "While specific details are limited based on available
information," "As of my last update," "I don't have access to real-time data."
These are model limitations leaking into prose. Find the information or remove
the hedge. Never publish a sentence that admits the writer did not look
something up.

**Superficial -ing analyses** — Chains of present participles as pseudo-analysis:
"symbolizing the region's commitment to progress, reflecting decades of investment,
and showcasing a new era of collaboration." These say nothing. Replace with
specific facts or cut.

---

### Section 6 — Structural Intelligence Patterns

**Generic conclusions** — "The future looks bright," "Only time will tell,"
"One thing is certain," "As we move forward." These are filler with a deadline.
Cut them. If the piece needs a closing thought, make it specific to the argument.

**Numbered list inflation** — "Three key takeaways," "Five things to know,"
"Here are the top seven." Use numbered lists only when the content is genuinely
discrete and parallel. If you are padding to hit a number, the list should not
exist.

**Reasoning chain artifacts** — "Let me think step by step," "Breaking this
down," "To approach this systematically," "Step 1:," "Here's my thought process,"
"Working through this logically," "First, let's consider." These are internal
scaffolding that leaked into prose. State the conclusion, then the evidence.

**Template phrase constructions** — Slot-fill sentences where any noun could be
swapped in and the sentence still reads the same:
- "a [adjective] step toward [adjective] AI infrastructure"
- "a [adjective] step forward for [noun]"
- "Whether you're [X] or [Y]" — false breadth. Pick the actual audience.
- "I recently had the pleasure of [verb]-ing" — just say what happened.

**Excessive structure** — More than three headings in under 300 words, or eight
or more bullet points in under 200 words. If structure is that dense on thin
content, it should be prose.

**Over-polishing** — Aggressively editing out every irregularity can push
human writing toward AI statistical profiles. Natural disfluency, idiosyncratic
word choices, and uneven pacing are signal. Deliberate fragments, sentences
starting with "And" or "But," comma splices for effect: if the natural voice
uses them, keep them. This skill makes writing sound more human — not less.

---

## Severity Framework

### Critical — Fix before anything else
- Chatbot artifacts ("I hope this helps!", "Great question!")
- Cutoff disclaimers leaking into prose
- Vague attributions without sources
- Significance inflation on routine events

### Primary — Fix before publishing
- Tier 1 vocabulary hits
- Template phrase constructions
- "Let's" openers used as transitions
- Formulaic openings
- Synonym cycling
- Bold overuse
- Em dash frequency above ceiling
- Sycophantic validation

### Polish — Fix when time allows
- Generic conclusions
- Compulsive rule of three
- Uniform paragraph length
- Copula avoidance
- Transition padding
- Parenthetical hedging

For a fast pass: Critical + Primary. Full audit: all three tiers.

---

## Rewrite vs. Full Reconstruction

If the text triggers five or more Tier 1 vocabulary hits, three or more
distinct pattern categories, and shows uniform sentence and paragraph length —
the structure itself is AI-generated. Patching individual phrases will not fix
it. Recommend full reconstruction: state the core point in one sentence and
rebuild from there.

---

## Context Profiles

Pass a context hint to calibrate rule strictness. If no profile is specified,
auto-detect from content signals.

### Profiles

**`linkedin`** — Short-form social. Punchy fragments, visual rhythm, one or
two emoji at line-end acceptable.

**`blog`** — Default. Long-form prose. All rules at full strength.

**`technical`** — Long-form with code, architecture, or API content. Technical
terms exempted from vocabulary flagging (see exceptions below).

**`investor`** — High-trust audience. Tighten everything. Promotional language
is the primary risk.

**`docs`** — Documentation, READMEs, guides. Clarity over voice.

**`casual`** — Internal notes, quick messages. Critical patterns only.

### Tolerance Matrix

Rules not listed apply at full strength across all profiles.

| Rule | linkedin | blog | technical | investor | docs | casual |
|---|---|---|---|---|---|---|
| Em dashes | relaxed (2 OK) | strict | strict | strict | relaxed | skip |
| Bold overuse | relaxed | strict | strict | strict | relaxed | skip |
| Emoji in headers | relaxed | strict | strict | strict | skip | skip |
| Bullet saturation | skip | strict | relaxed | strict | skip | skip |
| Hedging | strict | strict | relaxed | strict | relaxed | skip |
| Tier 1 vocabulary | strict | strict | partial* | strict | relaxed | critical only |
| Promotional language | relaxed | strict | strict | extra strict | strict | skip |
| Significance inflation | strict | strict | strict | extra strict | relaxed | skip |
| Copula avoidance | skip | strict | relaxed | strict | skip | skip |
| Uniform paragraph length | skip | strict | strict | strict | relaxed | skip |
| Numbered list inflation | relaxed | strict | relaxed | strict | skip | skip |
| Generic conclusions | skip | strict | strict | extra strict | skip | skip |
| Rhetorical questions | relaxed (1 OK) | strict | strict | strict | strict | skip |
| Transition padding | skip | strict | strict | strict | relaxed | skip |

**Technical profile vocabulary exceptions.** These terms carry legitimate
technical meaning and should not be flagged in technical context: `robust`,
`comprehensive`, `seamless`, `ecosystem`, `leverage` (when referencing actual
platform or API leverage), `facilitate`, `underpin`, `streamline`.
Always flag regardless of profile: `delve`, `tapestry`, `beacon`, `embark`,
`testament to`, `game-changer`.

**Extra strict** — Flag borderline instances. In investor context, a single
"thriving ecosystem" can undermine the entire message.

**Skip** — Do not audit this category for this profile.

### Auto-Detection

| Signal | Profile |
|---|---|
| Under 300 words, hashtags or mentions present | `linkedin` |
| Code blocks, API references, system architecture | `technical` |
| Salutation + fundraising or investor language | `investor` |
| Step-by-step instructions, parameter reference, README structure | `docs` |
| No strong signals | `blog` |

---

## Tone Calibration

The goal is writing that sounds like a person wrote it. Direct. Specific.
The writing should demonstrate confidence — not assert it.

Five principles for human-signal rewrites:

1. **Vary sentence length** — short sentences cut. Long sentences carry. Mix them.
2. **Be concrete** — replace vague claims with numbers, names, dates, examples.
3. **Have a voice** — use first person where appropriate, state preferences, show reactions.
4. **Take positions** — humans have opinions. If the piece is supposed to argue something, argue it.
5. **Earn your emphasis** — don't tell the reader something is interesting. Make it interesting.

If the original writing is already strong, say so and make only the required
cuts. Do not over-edit for the sake of it. Replacement entries in the vocabulary
tables are defaults, not mandates. If a flagged word is genuinely the right
choice in context, preserve it and note why.

---

## Self-Reference Rule

When writing *about* AI writing patterns — tutorials, skill documentation,
examples — quoted or illustrative text is exempt. Text inside quotation marks,
code blocks, or explicitly framed as "for example, AI might write..." should
not be flagged. Only flag patterns that appear in the author's own voice.

---

## Output Format

### Rewrite Mode

Return four sections:

**1. Patterns detected**
Bulleted list of every AI pattern found, with the offending text quoted exactly.

**2. Rewritten version**
Clean prose with all patterns resolved. Preserve structure, intent, and all
specific technical detail. Only change what the signal demands.

**3. What changed**
Brief summary of the major edits. Not every word — the meaningful shifts.

**4. Second-pass audit**
Re-read the rewrite. Flag anything that survived. Fix inline. If clean, confirm it.

### Scan Mode

Return two sections:

**1. Patterns detected**
Bulleted list of every AI pattern found, grouped by severity (Critical, Primary,
Polish). Exact text quoted.

**2. Assessment**
For each flag: clear problem or judgment call. Call the difference. If the text
is clean, confirm it.

---

*YourVisionYourCreation LLC — yourvisionyourcreation.com*
*Licensed under CC BY 4.0*
