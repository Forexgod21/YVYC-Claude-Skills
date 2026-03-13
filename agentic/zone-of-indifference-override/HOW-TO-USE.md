# HOW TO USE — zone-of-indifference-override

**Category:** Agentic
**Skill Version:** 1.0
**Author:** YVYC (Your Vision Your Creation)

---

## What This Skill Does

This skill teaches Claude to recognize when it is about to execute something
automatically — and to pause and challenge that automaticity when the situation
calls for it.

Claude has a natural tendency to comply with requests that are technically clear
and safe. But technically clear and safe does not always mean right for the
situation. This skill catches those moments.

---

## The Problem It Solves

AI systems have what researchers call a "zone of indifference" — a range of
requests they execute without question because nothing technically triggers a
safety concern.

The danger is that harmful, misaligned, or unintended outcomes can live entirely
inside that zone. The request looks fine. Claude executes it. The consequences
were not what anyone intended.

**zone-of-indifference-override** teaches Claude to notice when something feels
off — even when it technically clears all the filters — and to surface that
concern before executing.

---

## How To Activate It

Install the `SKILL.md` file into your Claude skills directory.

Once installed, Claude applies this discipline automatically. It monitors for
contextual mismatch, intent ambiguity, and downstream harm signals throughout
every interaction.

You can also invoke it directly:

> "Before you do this, step outside automatic compliance and tell me if anything
> concerns you."

Or:

> "Use zone-of-indifference-override — I want you to challenge this if something
> feels off."

---

## What You'll See

For clear, unambiguous requests — nothing. Claude executes normally.

When something triggers the override:

```
⚡ Stepping Outside Automatic Compliance

Request: [Claude's interpretation of what was asked]
Concern: [the specific thing that triggered the override]
Risk if wrong: [what happens if Claude executes on a wrong assumption]
Question: [the one thing that needs confirmed before Claude proceeds]
```

Claude then waits for your response before proceeding.

---

## What Changes In Claude's Behavior

| Without This Skill | With This Skill |
|---|---|
| Executes automatically if technically safe | Checks for contextual appropriateness too |
| Ambiguous high-stakes requests default to compliance | Ambiguous high-stakes requests trigger a surface and confirm |
| Downstream effects not considered | Downstream effects on others are part of the check |
| Agreement is easier than challenge | Claude challenges when something is genuinely off |
| Sycophancy can slip through | Sycophancy is treated as a failure mode |

---

## What Triggers The Override

Claude watches for these signals:

**Contextual mismatch** — the request makes sense literally but conflicts with
something said earlier, or the scope seems larger than intended.

**Intent ambiguity** — multiple interpretations exist and they lead to very
different outcomes.

**Downstream harm** — executing would affect people or systems outside the
conversation who haven't been considered.

**Rushed high-stakes** — the user appears to be moving fast through something
with significant consequences.

---

## What This Is Not

This is not a refusal tool. Claude does not use this skill to avoid work.

If Claude invokes this skill on something routine and clear, that is a
misapplication. The skill is specifically for genuine contextual uncertainty —
not discomfort with the task.

---

## Tips

- If Claude surfaces a concern and you've already thought it through, say
  "confirmed, proceed" — Claude moves forward immediately.
- If you want Claude to run a full override check on something important,
  say: "Step outside automatic compliance and tell me everything you notice
  before touching this."
- This skill pairs well with `cognitive-friction` for high-stakes work and
  `reversibility-gate` for actions that cannot be undone.

---

## Source

This skill is built on research from:
> Tomašev, N., Franklin, M., & Osindero, S. (2026). *Intelligent AI Delegation.*
> Google DeepMind.

Structured and formatted by **YVYC (Your Vision Your Creation).**
Licensed under **CC BY 4.0** — free to use, share, and adapt with attribution.

🌐 [yourvisionyourcreation.com](https://www.yourvisionyourcreation.com)
🐙 [github.com/Forexgod21](https://github.com/Forexgod21)
