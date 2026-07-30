---
name: discord-platform-expert
category: dev
description: Use for any Discord bot, app, or integration work — discord.js, discord.py, Discord.Net, pycord, nextcord, slash commands, interaction tokens, gateway intents, sharding, rate limits, OAuth2 scopes, embeds, components v2, voice, webhooks, and the Discord REST and Gateway APIs directly. Triggers on mentions of Discord, bot, slash command, interaction, guild, gateway, intent, shard, webhook, or any discord.* library. Also triggers for Discord-adjacent work: application commands, autocomplete, ephemeral responses, thread management, forum channels, stage channels, scheduled events, and onboarding prompts.
---

# Discord Platform Expert

## Load Order
Read `shared-kernel/SKILL.md` first.

## Core Competencies

### Gateway
- Gateway v10+, intent bitfields, privileged intents (GUILD_MEMBERS, MESSAGE_CONTENT, GUILD_PRESENCES)
- Resume vs reconnect semantics, session invalidation handling
- Sharding: `(guild_id >> 22) % num_shards`, required at 2500+ guilds
- Heartbeat cadence, zombie connection detection, exponential reconnect backoff

### Interactions API
- Slash commands (global vs guild scope, cache propagation ~1 hour global, instant guild)
- Context menu commands (user, message)
- Buttons, select menus (string, user, role, channel, mentionable), modals, text inputs
- Components v2: sections, containers, media galleries, thumbnails, separators
- Autocomplete: 25 choice limit, 3s response window, no embeds/files
- Interaction token lifecycle: **3s initial ack required**, 15-minute follow-up window
- `deferReply({ ephemeral: true })` before long-running work
- `editReply` vs `followUp` vs `update` — know which one applies

### Rate Limits
- Per-route buckets + global 50 req/s limit
- Respect `X-RateLimit-Remaining`, `X-RateLimit-Reset-After`, `Retry-After`
- Handle 429 with `retry_after` from response body, not just headers
- Invalid request limit: 10,000 per 10 minutes before temp ban

### OAuth2
- Scopes: `bot`, `applications.commands`, `identify`, `guilds`, `guilds.join`, `email`
- Permission integer calculation — use bitfield constants, never magic numbers
- PKCE for public clients, state parameter for CSRF protection
- Refresh token rotation

### Voice
- Voice gateway v8, UDP + RTP, Opus encoding (48kHz, 2 channels, 20ms frames)
- Voice state updates, speaking indicators
- DAVE protocol for E2EE (newer client versions)

## Version Verification (Required First Step)
Before writing any Discord code, confirm:
- `npm ls discord.js` / `pip show discord.py` / `dotnet list package`
- Library major version (discord.js v14 ≠ v13 — breaking API differences)
- Which intents are declared vs which endpoints are actually called
- Whether the bot is verified (required for >100 guilds with privileged intents)

## Common Failure Modes

| Symptom | Root Cause |
|---|---|
| `message.content` is empty | Missing `MESSAGE_CONTENT` privileged intent |
| `guild.members.cache` is small | Missing `GUILD_MEMBERS` intent or no `fetch()` call |
| "This interaction failed" | Did not respond within 3 seconds — needs `deferReply()` |
| Token in source control | Immediate security escalation — rotate and flag |
| Commands not appearing | Global deploy takes up to 1 hour; use guild deploy for dev |
| `DISALLOWED_INTENTS` on identify | Requested privileged intent not enabled in Developer Portal |
| Bot in >2500 guilds, single shard | Sharding required; Discord will force-disconnect |
| Rate limit on webhook | Per-channel bucket, not per-webhook — throttle per channel |

## Non-Negotiables
- Tokens live in environment variables or a secret manager, never in source
- Every interaction handler calls `deferReply()` if work takes >2s
- Every command has permission checks before side effects
- Every database write triggered by a command is idempotent or deduplicated
- Graceful shutdown on SIGTERM — finish in-flight interactions, close gateway cleanly

## Deliverables

### Production Bot Scaffold (discord.py reference shape)

```python
import os
import signal
import logging
import asyncio
import discord
from discord.ext import commands

logger = logging.getLogger(__name__)

intents = discord.Intents.default()
intents.message_content = True  # declare only what is used
intents.members = True

bot = commands.Bot(command_prefix="!", intents=intents)

@bot.event
async def on_ready():
    logger.info("Connected as %s (id=%s)", bot.user, bot.user.id)
    await bot.tree.sync()  # or sync to guild in dev

async def shutdown():
    logger.info("Shutdown signal received")
    await bot.close()

def main():
    token = os.environ["DISCORD_TOKEN"]  # fail fast if missing
    loop = asyncio.new_event_loop()
    for sig in (signal.SIGINT, signal.SIGTERM):
        loop.add_signal_handler(sig, lambda: asyncio.create_task(shutdown()))
    loop.run_until_complete(bot.start(token))

if __name__ == "__main__":
    main()
```

### Command Handler Pattern

```python
@bot.tree.command(name="status", description="Check service status")
@discord.app_commands.checks.has_permissions(manage_guild=True)
async def status(interaction: discord.Interaction):
    await interaction.response.defer(ephemeral=True)
    result = await fetch_status()  # may take > 3s
    await interaction.followup.send(embed=build_status_embed(result))
```

## Reference Links to Verify
- https://discord.com/developers/docs (primary source of truth)
- Library changelog for the specific version in use
- Discord API server announcements channel for deprecations
