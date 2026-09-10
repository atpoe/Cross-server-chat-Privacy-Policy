# Privacy Policy — CrossServerChat

**Last updated:** 10 September 2026  
**Mod / Discord application:** CrossServerChat  
**Author:** Poe

This policy covers the CrossServerChat Minecraft Forge mod and the Discord bot a server hoster may create to run it.

## Summary

CrossServerChat does **not** collect, sell, or send personal information to the mod author. There is no telemetry, no analytics, no account system, and no remote database operated by the author.

Anything the mod handles stays on **the hoster’s Minecraft server** and on **Discord**, under that hoster’s control. Use of the mod on a public server is **at the hoster’s will**: the hoster chooses to install it, which Discord channels to use, how long logs are kept, and who can see chat.

## Who is responsible

- **The mod author** does not receive player names, chat, IP addresses, Discord IDs, or server logs from this mod.
- **The server hoster** (the person or team running the Minecraft server) is responsible for how the mod is configured and for any data that appears in their console, log files, or Discord server.
- **Discord** processes messages that pass through Discord according to [Discord’s Privacy Policy](https://discord.com/privacy). This mod does not replace Discord’s policy.

## What the mod does on the hoster’s machine

When a hoster installs CrossServerChat and supplies their own Discord bot token, the mod may:

- Read chat in Discord channels the hoster configured, so messages can be shown in Minecraft
- Post Minecraft chat, optional join/leave lines, TAB roster text, and `/server_all` command packets to those channels
- Keep small local files under `config/CrossServerChat/` on the hoster’s server (for example config, a local server id, and the Discord message id used for TAB)

That processing happens only so linked worlds can share chat and TAB. It is not used to profile players or to build a dataset for the author.

## What is not collected by the author

The author does **not**:

- Collect or store player UUIDs, names, chat, or IPs
- Collect Discord user IDs, usernames, or message content
- Run crash reporters, usage stats, or update pings that send personal data
- Share or sell any user information (there is none held by the author)

## Players

If you play on a server that uses this mod:

- Your in-game chat may be copied to a Discord channel the **hoster** chose, and Discord chat in that channel may appear in-game
- Other linked Minecraft worlds the hoster connected may see the same chat
- Whether that happens, who can read it, and how long it is kept is decided by the **hoster** and by Discord — not by the mod author

If you do not want your chat bridged, leave that server or ask the hoster. The author cannot turn the bridge off on someone else’s server.

## Hosters

You control the bot token, channel IDs, webhooks, and server logs. Do not share bot tokens or webhook URLs. Delete the bot and config files if you stop using the mod. Discord message retention follows your Discord server’s settings.

## Contact

Questions about this policy: contact the hoster of the Minecraft server you play on, or the Discord application owner listed in the Discord Developer Portal. The author does not operate a data-collection service for this mod.

## Changes

If this policy changes, the date at the top of this file will be updated.
