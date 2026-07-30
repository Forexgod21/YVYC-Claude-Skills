# Discord Platform Expert — How To Use

**Skill:** `discord-platform-expert`
**Category:** Dev
**Author:** YourVisionYourCreation LLC
**License:** CC BY 4.0

---

## What This Skill Does

Discord Platform Expert makes Claude build Discord bots and integrations
that survive contact with the real platform — gateway intents, the
3-second interaction acknowledgment window, per-route rate limit buckets,
sharding thresholds, OAuth2 scopes, and components v2 — across discord.js,
discord.py, and the raw REST and Gateway APIs.

---

## The Problem It Solves

Discord has platform rules that generic bot tutorials never mention, and
every one of them is a production incident waiting for you:

- Miss the 3-second interaction ack → "This interaction failed" for every
  user
- Forget the `MESSAGE_CONTENT` privileged intent → `message.content`
  silently empty
- Deploy global slash commands during development → wait an hour to see
  each change
- Cross 2,500 guilds on a single shard → Discord force-disconnects the bot
- Blow the invalid-request limit → temporary ban

This skill knows all of it in advance, and its failure-mode table maps
each symptom straight to its cause.

---

## Quick Start

```
Build a slash command that queries an API and replies with an embed —
production-grade, ephemeral response.
```
```
My bot says "This interaction failed" randomly — diagnose it.
```
```
Set up the bot scaffold: intents, graceful shutdown, guild-scoped
command sync for dev.
```
```
We just passed 2,000 servers — get me ready for sharding.
```

---

## Key Disciplines

| Area | The Rule |
|---|---|
| Version check first | Confirms library major version before writing — discord.js v14 ≠ v13 |
| Interactions | `deferReply()` before anything that could exceed 2 seconds |
| Intents | Declare only what's used; know which three are privileged |
| Rate limits | Respect the bucket headers and the 429 body, not just one of them |
| Tokens | Environment or secret manager — a token in source is an immediate rotate-and-flag |
| Commands | Permission checks before side effects; idempotent database writes |

---

## What This Skill Will Not Do

- Ship a handler that can miss the 3-second acknowledgment window
- Request privileged intents the code never uses
- Put a bot token anywhere near source control
- Use global command deploys for development iteration

---

## Installation

1. Copy the `SKILL.md` file from this folder
2. Place it in your Claude skills directory
3. Install `shared-kernel` (from `agentic/`) alongside it — this skill
   loads it first
4. It activates automatically on any Discord bot, slash command, gateway,
   or webhook task

---

*Part of the YVYC Claude Skills Library — Dev Category*
*YourVisionYourCreation LLC — [yourvisionyourcreation.com](https://www.yourvisionyourcreation.com)*
*Licensed under CC BY 4.0 — Free to use with attribution to YourVisionYourCreation LLC*
