# HOW TO USE — contract-first-decomposition

**Category:** Agentic
**Skill Version:** 1.0
**Author:** YVYC (Your Vision Your Creation)

---

## What This Skill Does

This skill teaches Claude to define what success looks like **before** starting any complex task — and to confirm that success was actually achieved when it finishes.

Without this skill, Claude will often complete tasks confidently while the output drifts from what you actually needed. This skill closes that gap.

---

## The Problem It Solves

You ask Claude to do something complex. Claude does it. You get an answer.

But was it right? Did it match what you actually needed? Did Claude check?

Most of the time — no. Claude completed the task based on its interpretation, delivered output that seemed reasonable, and moved on.

**contract-first-decomposition** forces Claude to lock in the target before firing, and confirm the hit afterward.

---

## How To Activate It

Install the `SKILL.md` file into your Claude skills directory.

Once installed, Claude will automatically activate this skill when you give it complex, multi-step, or consequential tasks.

You can also manually trigger it by saying:

> "Use contract-first-decomposition on this task."

Or simply:

> "Before you start, tell me what success looks like and how you'll verify it."

---

## What You'll See

For any non-trivial task, Claude will output a **Pre-Task Contract** before starting:

```
Pre-Task Contract
- Task: [Claude's interpretation]
- Success Looks Like: [specific, measurable outcome]
- Verification Method: [how it will be confirmed]
- Complexity: [simple / moderate / complex]
- Decomposition Required: [yes / no]
```

For simple tasks, Claude skips the format and just applies the discipline quietly.

---

## What Changes In Claude's Behavior

| Without This Skill | With This Skill |
|---|---|
| Starts immediately, figures out success later | Defines success before starting |
| Declares completion based on feeling | Confirms completion against stated criteria |
| Silently shifts scope mid-task | Flags scope changes and re-states criteria |
| Breaks tasks into steps without checking if steps are verifiable | Only proceeds on verifiable sub-tasks |
| Treats irreversible actions the same as reversible ones | Stops and confirms before any irreversible action |

---

## Real Examples

**Good prompt to use this with:**
- "Write a complete outline for my nonprofit grant proposal."
- "Build me a trading journal template in Excel."
- "Analyze this document and give me a risk summary."
- "Refactor this function so it handles edge cases."

**Prompts where this skill won't activate (too simple):**
- "What does MCP stand for?"
- "Summarize this paragraph."
- "What day is it?"

---

## Tips

- If Claude's Pre-Task Contract doesn't match your actual intent — correct it **before** Claude starts. That's the whole point of the contract.
- If Claude declares success but the output feels off — reference the contract and ask Claude to verify against it.
- For long projects, you can ask Claude to re-state the contract at each major phase.

---

## Source

This skill is built on research from:
> Tomašev, N., Franklin, M., & Osindero, S. (2026). *Intelligent AI Delegation.* Google DeepMind.

Structured and formatted by **YVYC (Your Vision Your Creation).**
Licensed under **CC BY 4.0** — free to use, share, and adapt with attribution.

🌐 [yourvisionyourcreation.com](https://www.yourvisionyourcreation.com)
🐙 [github.com/Forexgod21](https://github.com/Forexgod21)
