# HOW TO USE — reversibility-gate

**Category:** Agentic
**Skill Version:** 1.0
**Author:** YVYC (Your Vision Your Creation)

---

## What This Skill Does

This skill forces Claude to stop and ask for your confirmation before taking any
action that cannot be undone.

Sending emails. Deleting files. Publishing content. Submitting forms. Making API
calls with real effects. All of these get a hard stop and a confirmation gate before
Claude touches them.

---

## The Problem It Solves

AI moves fast. That's usually good. But fast and irreversible is a dangerous
combination.

Without this skill, Claude can interpret a broad instruction — "go ahead and send
that" — as permission for everything downstream, including actions you didn't
specifically authorize in the moment.

**reversibility-gate** breaks that pattern. Every irreversible action gets its own
confirmation. No assumed consent. No surprises.

---

## How To Activate It

Install the `SKILL.md` file into your Claude skills directory.

Once installed, Claude will automatically gate irreversible actions — you don't need
to do anything special. The skill runs in the background and only surfaces when it
needs to.

You can also manually invoke it by saying:

> "Before you do anything irreversible, stop and ask me first."

Or:

> "Use reversibility-gate on this task."

---

## What You'll See

When Claude is about to take an irreversible action, it will stop and show you this:

```
⚠️ Irreversible Action — Confirmation Required

Action: [what is about to happen]
Effect: [what changes and cannot be undone]
Scope: [what is affected]

Type YES to confirm, or tell me to stop.
```

For reversible actions — drafting, writing, analyzing, planning — Claude proceeds
silently. No unnecessary interruptions.

---

## What Changes In Claude's Behavior

| Without This Skill | With This Skill |
|---|---|
| Executes irreversible actions based on implied consent | Stops and confirms every irreversible action explicitly |
| Treats "go ahead" as blanket permission | Requires specific confirmation at the moment of action |
| May retry failed actions automatically | Requires re-confirmation before retrying |
| Uncertain actions default to proceeding | Uncertain actions default to gating |

---

## How It Works With Other Skills

This skill pairs directly with **contract-first-decomposition**.

When you use both together:
- `contract-first-decomposition` flags irreversible sub-tasks **during planning**
  before work begins
- `reversibility-gate` enforces the hard stop **during execution** when those
  sub-tasks are reached

Together they cover both ends — you know what's irreversible before you start, and
Claude still gates it when it arrives.

---

## Real Examples

**Irreversible — gate activates:**
- "Send this email to the client list"
- "Delete these old records from the database"
- "Post this to my LinkedIn"
- "Submit the form"
- "Overwrite the existing file"

**Reversible — gate does not activate:**
- "Draft an email to the client list"
- "Write a script that would delete these records"
- "Write a LinkedIn post for my review"
- "Fill in the form fields so I can check it"
- "Create a new version of the file"

See the pattern — **drafting and creating is reversible, executing and sending is not.**

---

## Tips

- If Claude gates something you consider routine, you can confirm quickly with YES
  and keep moving. The gate is a speed bump, not a roadblock.
- If you want Claude to have broader autonomy for a specific session, say so
  explicitly — "you have my standing approval for file saves in this project."
  Claude will note it and apply it accordingly.
- For long multi-step tasks, the gate will appear each time an irreversible action
  is reached — not just once at the start.

---

## Source

This skill is built on research from:
> Tomašev, N., Franklin, M., & Osindero, S. (2026). *Intelligent AI Delegation.*
> Google DeepMind.

Structured and formatted by **YVYC (Your Vision Your Creation).**
Licensed under **CC BY 4.0** — free to use, share, and adapt with attribution.

🌐 [yourvisionyourcreation.com](https://www.yourvisionyourcreation.com)
🐙 [github.com/Forexgod21](https://github.com/Forexgod21)
