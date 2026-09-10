CrossServerChat:
CrossServerChat is a simple yet powerful serverside networking tool that links chat, TAB, and operator commands across multiple Minecraft worlds through Discord. Player chat uses one channel. TAB and /server_all can use a second hidden channel. The mod is server-only, so players do not need to install anything. Each world keeps its own identity with a [ServerName] tag. No proxy, Redis, or Velocity setup is required. The author collects no player or Discord data; see PRIVACY.md and TERMS.md. What happens on a live server is at the hoster's will.

Cross-Server Chat:
- Share player chat across every linked world in the format [Camelot] Poe: hello
- Optional Discord webhook so messages use the player's name and skin
- Optional Discord-to-Minecraft chat as [Discord] name: message
- Optional join and leave broadcasts on every linked world
- Works beside Discord Integration when you use a different bot and a different channel
- Loop-safe identity so a world never echoes its own messages back to itself

Network TAB:
- Custom header and footer with Minecraft color codes
- Live network list with %worlds%, player counts, and TPS
- Per-viewer name colors: you can be gold while other players stay white
- Visual HTML editor written to config/CrossServerChat/tab-editor.html
- Instant apply with /cross_server reload, no server restart
- Optional ranks from ranks.toml, e.g. [Dev] AtPoe in chat and TAB

Network Commands:
- /server_all <command> plus /y confirmation to run an operator command on every linked world
- /cross_server reload and /csc reload to reload config.toml, tab.toml, and ranks.toml
- /server_all packets go to the protocol channel (or the chat channel if protocolChannelId is empty) and are removed after other worlds have read them. TAB keeps one edited roster message there.

Setup Guide:

1. Install the mod
- Use Minecraft Forge 1.20.1
- Put only cross_server_chat-1.2.1.jar in the mods folder of every world you want linked
- Clients do not need the jar
- Start each server once so it creates config/CrossServerChat/

2. Create a Discord bot
- Open the Discord Developer Portal and create a new application
- Open Bot, create the bot, and copy the token
- Enable Message Content Intent
- Invite the bot with View Channel, Send Messages, Read Message History, and Manage Messages
- Do not reuse the Discord Integration bot

3. Create Discord channels
- Make a channel for player chat. Do not reuse the Discord Integration chat channel
- Optional: make a second hidden channel for TAB and /server_all so the chat channel stays clean
- Enable Discord Developer Mode, right-click each channel, and copy the Channel ID
- Invite the bot to both channels (View Channel, Send Messages, Read Message History, Manage Messages)
- Optional: create a webhook in the chat channel if you want player names and skins. The same webhook URL can be used on every world

4. Edit config/CrossServerChat/config.toml on every world
- serverName must be unique per world, for example Camelot, Tristram, Test
- botToken, channelId, protocolChannelId, and webhookUrl must be the same on every world
- protocolChannelId is the hidden TAB / /server_all channel. Leave empty to keep those in the chat channel
- allowDiscordChat = true if people should be able to talk from Discord into Minecraft
- broadcastJoin and broadcastLeave default to false
- hideCommandMessages = true keeps /server_all packets from sitting in the protocol channel
- Optional [serverList] enabled = true shows each linked world on the multiplayer player-count hover, e.g. Camelot: 10/20
- Run /cross_server reload or restart after saving

5. Edit TAB
- Open config/CrossServerChat/tab-editor.html in a browser
- Design the header, footer, world list, your TAB name color, and other players' TAB name color
- Copy or save the TOML into config/CrossServerChat/tab.toml
- Run /cross_server reload

6. Ranks
- Edit config/CrossServerChat/ranks.toml
- Put player names (or UUIDs) on a rank list
- Prefixes such as &b[Dev]&r  show in chat, TAB (%rank%), and Discord names
- Copy the same ranks.toml to every linked world
- Run /cross_server reload

7. Commands
- /cross_server reload or /csc reload — reload configs and refresh TAB
- /cross_server tab on|off — enable or disable custom TAB
- /server_all <command> then /y — run that command on every linked world (OP only)

Placeholders:
- %title% %subtitle% %server% %online% %local% %max% %tps%
- %worlds% %world% %count% %players% %player% %rank% %level% %chapter% %more%
- %rank% is the prefix from ranks.toml (empty if the player is on no list)
- %level% is Mine and Slash combat level when mineAndSlash = true
- %chapter% is the current FTB Quests chapter when ftbQuests = true (completed quests, not readme ticks)
- Optional ftbChapterMarkers in tab.toml sets start:end quest IDs per chapter; ftbQuestIds is only a filter when markers are empty
