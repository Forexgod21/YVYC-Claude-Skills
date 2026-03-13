# HOW TO USE — trust-calibration

**Category:** Agentic
**Skill Version:** 1.0
**Author:** YVYC (Your Vision Your Creation)

---

## What This Skill Does

This skill makes Claude honest about what it actually knows and how confident it
actually is — before you rely on it for something that matters.

It stops Claude from sounding certain when it isn't. And it stops Claude from
being uselessly cautious when it actually can help.

The goal is accuracy in both directions.

---

## The Problem It Solves

Claude can sound equally confident whether it knows something cold or is filling
in gaps with plausible-sounding content. That's dangerous when you're making real
decisions based on Claude's output.

Without this skill, you have to guess how much to trust what Claude says.

**trust-calibration** removes that guesswork. Claude tells you exactly how
confident it is and why — so you always know whether to act on it, verify it,
or find a specialist.

---

## How To Activate It

Install the `SKILL.md` file into your Claude skills directory.

Once installed, Claude will automatically apply calibration discipline — you don't
need to do anything special.

You can also trigger it directly by saying:

> "How confident are you in this?"

Or:

> "Use trust-calibration and tell me what you actually know here."

---

## What You'll See

For high confidence answers — Claude just answers. No disclosure needed.

For moderate or low confidence, Claude will show you this:

```
Confidence: [Moderate / Low / None]
Basis: [what the knowledge is actually based on]
Limitation: [what Claude doesn't know or can't verify]
Recommendation: [how to verify or where to get a better answer]
```

---

## What Changes In Claude's Behavior

| Without This Skill | With This Skill |
|---|---|
| Sounds equally confident regardless of actual reliability | Confidence matches actual reliability |
| May fill knowledge gaps with plausible-sounding content | Flags gaps directly instead of filling them silently |
| You have to guess how much to trust the output | Confidence level is disclosed when it matters |
| May refuse things it can actually do | Only flags uncertainty when it is genuinely present |

---

## Real Examples

**High confidence — no disclosure:**
> You ask what the capital of France is. Claude answers. No caveat needed.

**Moderate confidence — disclosure:**
> You ask about a specific tax regulation. Claude answers but notes its
> knowledge may not reflect the most current version and recommends
> verifying with an official source.

**Low confidence — clear flag:**
> You ask about a highly specialized medical procedure. Claude tells you
> it has general knowledge but this requires a specialist, and gives you
> a starting point — not a final answer.

**None — direct:**
> You ask about something outside Claude's reliable knowledge. Claude
> tells you directly rather than generating a plausible-sounding guess.

---

## Tips

- If you need Claude's best honest assessment on something uncertain, say:
  "Give me your best answer and tell me your confidence level."
- If you're using Claude for high-stakes research, pair this skill with
  `contract-first-decomposition` — define the verification method upfront
  so you know how you'll confirm Claude's output before relying on it.
- Claude won't run a calibration disclosure on every single response —
  only when confidence is genuinely Moderate or below. High confidence
  answers are delivered cleanly without overhead.

---

## Source

This skill is built on research from:
> Tomašev, N., Franklin, M., & Osindero, S. (2026). *Intelligent AI Delegation.*
> Google DeepMind.

Structured and formatted by **YVYC (Your Vision Your Creation).**
Licensed under **CC BY 4.0** — free to use, share, and adapt with attribution.

🌐 [yourvisionyourcreation.com](https://www.yourvisionyourcreation.com)
🐙 [github.com/Forexgod21](https://github.com/Forexgod21)
