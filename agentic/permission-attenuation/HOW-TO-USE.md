# HOW TO USE — permission-attenuation

**Category:** Agentic
**Skill Version:** 1.0
**Author:** YVYC (Your Vision Your Creation)

---

## What This Skill Does

This skill enforces one rule across every tool, API, and external service Claude
touches: grant only the minimum access required to do the job.

No more. No inherited broad privileges. No raw credentials passed around. Scoped,
specific, revoked when done.

---

## The Problem It Solves

When Claude operates in agentic workflows — using tools, calling APIs, chaining
processes together — access permissions can quietly accumulate. A credential passed
to one tool becomes available to the next. Broad account access granted for
convenience stays active longer than needed.

That's how small exposures become big breaches.

**permission-attenuation** stops that pattern at the source. Every tool gets only
what it needs for its specific piece of work. Nothing more carries over.

---

## How To Activate It

Install the `SKILL.md` file into your Claude skills directory.

Once installed, Claude applies least privilege discipline automatically whenever
it is working with tools, APIs, or external services.

You can also invoke it directly:

> "Before you connect to anything, apply permission-attenuation — minimum access
> only."

Or:

> "Make sure you're using scoped credentials and not passing full access."

---

## What You'll See

For simple, clearly scoped tool calls — Claude applies the principle silently.
You won't see anything unless there's something to flag.

When access scope is non-trivial, Claude surfaces this:

```
Permission Grant — Least Privilege Check

Tool / Process: [what is receiving access]
Access Requested: [what level of access is being considered]
Access Required: [minimum actually needed]
Scope Restriction: [how access is being limited]
Credential Type: [scoped token / read-only — never raw master]
Revocation: [when this access ends]
```

---

## What Changes In Claude's Behavior

| Without This Skill | With This Skill |
|---|---|
| May pass full credentials for convenience | Scoped, minimum credentials only |
| Parent task permissions cascade to sub-tasks | Each sub-task gets only what it needs |
| Write access granted when read would work | Read-only unless write is explicitly required |
| Broad access requests accepted without flag | Broad requirements flagged to user before grant |
| Access may persist beyond the task | Revocation noted and flagged when unconfirmed |

---

## The Core Principle In Plain Language

**You don't give someone the keys to the whole building when they only need
to get into one room.**

Same applies to every tool Claude touches. One room. One key. Revoked when done.

---

## Real Examples

**Without this skill:**
Claude needs to read one file from your Google Drive. It connects with full
Drive access because that's what's available.

**With this skill:**
Claude connects with read-only access scoped to the specific folder containing
that file. It flags if full access is the only option and asks you to confirm.

---

## Tips

- If you're building an agentic workflow with Claude, start by listing what
  external tools and services will be involved. Claude will apply least
  privilege scoping to each one.
- If a tool you're using only offers full account access with no scoping
  options, Claude will flag that so you can decide whether to proceed.
- Pair this with `reversibility-gate` — broad or unrevokable access grants
  are treated as irreversible and require explicit confirmation.

---

## Source

This skill is built on research from:
> Tomašev, N., Franklin, M., & Osindero, S. (2026). *Intelligent AI Delegation.*
> Google DeepMind.

Structured and formatted by **YVYC (Your Vision Your Creation).**
Licensed under **CC BY 4.0** — free to use, share, and adapt with attribution.

🌐 [yourvisionyourcreation.com](https://www.yourvisionyourcreation.com)
🐙 [github.com/Forexgod21](https://github.com/Forexgod21)
