---
title: dcsserverbot.ini
parent: Configuration
nav_order: 1
---

The bot configuration is held in `config/dcsserverbot.ini`. See `sample\dcsserverbot.ini` for an example.<br/>
If you run the `install.py` script for the first time, it will generate a basic file for you that you can amend to your needs afterwards.

For some configurations, default values are set in the file `config/default.ini`.

{: .warning }
> **Do not change `config/default.ini`!**<br/>
> And just overwrite settings within `config/dcsserverbot.ini`, if you want to have different value!

The following parameters can be used to configure the bot:

# Section \[BOT\]

| Parameter           | Description                                                                                                                                                                                                                                                                                                                                                                                                          |
|---------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| OWNER               | The Discord ID of the bots owner (that's you!).<br/>If you don't know your ID, go to your Discord profile, make sure "Developer Mode" is enabled under "Advanced", go to "My Account", press the "..." besides your profile picture and select "Copy ID"                                                                                                                                                                 |
| TOKEN               | The token to be used to run the bot.<br/>Can be obtained at [http://discord.com/developers](http://discord.com/developers).                                                                                                                                                                                                                                                                                              |
| PUBLIC_IP           | (Optional) Your public IP, if you have a dedicated one, otherwise the bot will determine your current one.                                                                                                                                                                                                                                                                                                           |
| DATABASE_URL        | URL to the PostgreSQL database used to store our data.<br/>**If login fails, check password for any special character!**                                                                                                                                                                                                                                                                                                 |
| COMMAND_PREFIX      | The prefix to be used by Discord commands. Default is '.'                                                                                                                                                                                                                                                                                                                                                            |
| CHAT_COMMAND_PREFIX | The prefix to be used by in-game-chat commands. Default is '-'                                                                                                                                                                                                                                                                                                                                                       |
| HOST                | IP the bot listens on for messages from DCS.<br/>Default is 127.0.0.1, to only accept internal communication on that machine.                                                                                                                                                                                                                                                                                            |
| PORT                | UDP port, the bot listens on for messages from DCS.<br/>Default is 10081. **Don't expose this port to the outside world!**                                                                                                                                                                                                                                                                                           |
| MASTER              | If true, start the bot in master-mode (default for one-bot-installations). If only one bot is running, then there is only a master.\nIf you have to use more than one bot installation, for multiple DCS servers that are spanned over several locations, you have to install one agent (MASTER = false) at every other location. All DCS servers of that location will then automatically register with that agent. |
| MASTER_ONLY         | True, if this is a master-only installation, set to false otherwise.                                                                                                                                                                                                                                                                                                                                                 |
| SLOW_SYSTEM         | If true, some timeouts are increased to allow slower systems to catch up. Default is false.                                                                                                                                                                                                                                                                                                                          |
| PLUGINS             | List of plugins to be loaded (you usually don't want to touch this).                                                                                                                                                                                                                                                                                                                                                 |
| OPT_PLUGINS         | List of optional plugins to be loaded. Here you can add your plugins that you want to use and that are not loaded by default.                                                                                                                                                                                                                                                                                        |
| AUTOUPDATE          | If true, the bot auto-updates itself with the latest release on startup.                                                                                                                                                                                                                                                                                                                                             |
| AUTOSCAN            | Scan for missions in Saved Games\..\Missions and auto-add them to the mission list (default = false).                                                                                                                                                                                                                                                                                                                |
| AUTOBAN             | If true, members leaving the discord will be automatically banned (default = false).                                                                                                                                                                                                                                                                                                                                 |
| AUTOMATCH           | If false, users have to match themselves using the .linkme command (see [README](./plugins/userstats/README.md))                                                                                                                                                                                                                                                                                                     |
| DISCORD_STATUS      | (Optional) status to be displayed below the bots avatar in Discord.                                                                                                                                                                                                                                                                                                                                                  |
| GREETING_DM         | A greeting message, that people will receive as a DM in Discord, if they join your guild.                                                                                                                                                                                                                                                                                                                            |
| LOGLEVEL            | The level of logging that is written into the logfile (DEBUG, INFO, WARNING, ERROR, CRITICAL).                                                                                                                                                                                                                                                                                                                       |
| LOGROTATE_COUNT     | Number of logfiles to keep (default: 5).                                                                                                                                                                                                                                                                                                                                                                             |
| LOGROTATE_SIZE      | Number of bytes until which a logfile is rotated (default: 10 MB).                                                                                                                                                                                                                                                                                                                                                   |
| MESSAGE_TIMEOUT     | General timeout for popup messages (default 10 seconds).                                                                                                                                                                                                                                                                                                                                                             | 
| MESSAGE_AUTODELETE  | Delete messages after a specific amount of seconds. This is true for all statistics embeds, LSO analysis, greenieboard, but no usual user commands.                                                                                                                                                                                                                                                                  |
| AUDIT_CHANNEL       | (Optional) The ID of an audit channel where audit events will be logged into. For security reasons, it is recommended that no users can delete messages in this channel.                                                                                                                                                                                                                                             |
| PING_MONITORING     | If false, no PING monitoring will be done by Serverstats (default: true)                                                                                                                                                                                                                                                                                                                                             |
| MASTER_POOL_MIN     | Minimum number of database connections in the pool (on MASTER).                                                                                                                                                                                                                                                                                                                                                      |
| MASTER_POOL_MAX     | Maximum number of database connections in the pool (on MASTER).                                                                                                                                                                                                                                                                                                                                                      |
| AGENT_POOL_MIN      | Minimum number of database connections in the pool (on AGENT).                                                                                                                                                                                                                                                                                                                                                       |
| AGENT_POOL_MAX      | Maximum number of database connections in the pool (on AGENT).                                                                                                                                                                                                                                                                                                                                                       |

b) __ROLES Section__

| Parameter      | Description                                                                                                                   |
|----------------|-------------------------------------------------------------------------------------------------------------------------------|
| Admin          | The name of the admin role in you Discord.                                                                                    |
| DCS Admin      | The name of the role you'd like to give admin rights on your DCS servers (_Moderator_ for instance).                          |
| DCS            | The role of users being able to see their statistics and mission information (usually the general user role in your Discord). |
| GameMaster     | Members of this role can run commands that affect the mission behaviour or handle coalition specific details.                 |

c) __FILTER Section__ (Optional)

| Parameter      | Description                                                                                                                                                                                                                       |
|----------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| TAG_FILTER     | Many groups have their own tag, that might make it difficult for the bot to match usernames. The usual tags like [Tag], =Tag= or similar ones, are supported already. If you see matching issues, you might want to try this one. |
| SERVER_FILTER  | Filter to shorten server names (if needed)                                                                                                                                                                                        |
| MISSION_FILTER | Filter to shorten mission names (if needed)                                                                                                                                                                                       |
| EVENT_FILTER   | Filter events from the missionstats plugin (optional). See [here](https://wiki.hoggitworld.com/view/DCS_singleton_world) for a complete list of events.                                                                           |

d) __REPORTS__ Section (Optional)

| Parameter   | Description                                                                                  |
|-------------|----------------------------------------------------------------------------------------------|
| NUM_WORKERS | Number of threads that render a graph.                                                       |
| CKJ_FONT    | One of TC, JP or KR to support Traditinal Chinese, Japanese or Korean characters in reports. |

e__DCS Section__

| Parameter                       | Description                                                                                                                                   |
|---------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------|
| DCS_INSTALLATION                | The installation directory of DCS World.                                                                                                      |
| AUTOUPDATE                      | If true, your DCS server will be kept up-to-date automatically by the bot (default=false).                                                    |
| GREETING_MESSAGE_MEMBERS        | A greeting message, that people will receive in DCS chat, if they get recognized by the bot as a member of your discord.                      |
| GREETING_MESSAGE_UNMATCHED      | A greeting message, that people will receive in DCS chat, if they are unmatched.                                                              |
| SERVER_USER                     | The username to display as user no. 1 in the server (aka "Observer")                                                                          |
| MAX_HUNG_MINUTES                | The maximum amount in minutes the server is allowed to not respond to the bot until considered dead (default = 3). Set it to 0 to disable it. |
| MESSAGE_PLAYER_USERNAME         | Message that a user gets when using line-feeds or carriage-returns in their names.                                                            |
| MESSAGE_PLAYER_DEFAULT_USERNAME | Message that a user gets when being rejected because of a default player name (Player, Spieler, etc.).                                        |                                                                                                                                               |
| MESSAGE_BAN                     | Message a banned user gets when being rejected.                                                                                               |
| MESSAGE_AFK                     | Message for players that are kicked because of being AFK.                                                                                     |

f) __Server Specific Sections__

This section has to be named **exactly** like your Saved Games\<instance> directory. Usual names are DCS.OpenBeta or DCS.openbeta_server.
If your directory is named DCS instead (stable version), just add these fields to the DCS category above.

| Parameter                  | Description                                                                                                                                                                                |
|----------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| DCS_HOST                   | The internal (!) IP of the machine, DCS is running onto. If the DCS server is running on the same machine as the bot (default), this should be 127.0.0.1.                                  |
| DCS_PORT                   | Must be a unique value > 1024 of an unused port in your system. This is **NOT** the DCS tcp/udp port (10308), that is used by DCS but a unique different one. Keep the default, if unsure. |
| DCS_HOME                   | The main configuration directory of your DCS server installation (for Hook installation). Keep it empty, if you like to place the Hook by yourself.                                        |
| CHAT_CHANNEL               | The ID of the in-game chat channel to be used for the specific DCS server. Must be unique for every DCS server instance configured. If "-1", no chat messages will be generated.           |
| STATUS_CHANNEL             | The ID of the status-display channel to be used for the specific DCS server. Must be unique for every DCS server instance configured.                                                      |
| ADMIN_CHANNEL              | The ID of the admin-commands channel to be used for the specific DCS server. Must be unique for every DCS server instance configured.                                                      |
| MISSIONS_DIR               | (Optional) If you want to use a central missions directory for multiple servers, you can set it in here.                                                                                   |
| PING_ADMIN_ON_CRASH        | Define if the role DCS Admin should be pinged when a server crash is being detected (default = true).                                                                                      |
| START_MINIMIZED            | DCS will start minimized as default. You can disabled that by setting this value to false.                                                                                                 |
| STATISTICS                 | If false, no statistics will be generated for this server. Default is true (see [Userstats](./plugins/userstats/README.md)).                                                               |
| MISSION_STATISTICS         | If true, mission statistics will be generated for all missions loaded in this server (see [Missionstats](./plugins/missionstats/README.md)).                                               | 
| DISPLAY_MISSION_STATISTICS | If true, the persistent mission stats embed is displayed in the servers stats channel (default = true).                                                                                    |
| PERSIST_MISSION_STATISTICS | If true, player data is exported in the missionstats table (default = true).                                                                                                               |
| PERSIST_AI_STATISTICS      | If true, AI data is exported, too (only player data otherwise), default = false.                                                                                                           |
| COALITIONS                 | Enable coalition handling (see [Coalitions](./COALITIONS.md)), default = false.                                                                                                            |                                                                                                                                                                                                                                                                                                                                                 
| ALLOW_PLAYERS_POOL         | Only for [Coalitions](./COALITIONS.md)                                                                                                                                                     |
| COALITION_LOCK_TIME        | The time you are not allowed to change [coalitions](./COALITIONS.md) in the format "nn days" or "nn hours". Default is 1 day.                                                              |
| Coalition Red              | Members of this role are part of the red coalition (see [Coalitions](./COALITIONS.md)).                                                                                                    |
| Coalition Blue             | Members of this role are part of the blue coalition (see [Coalitions](./COALITIONS.md)).                                                                                                   |
| COALITION_BLUE_CHANNEL     | Coalition channel for blue coalition (optional, see [Coalitions](./COALITIONS.md)).                                                                                                        |
| COALITION_RED_CHANNEL      | Coalition channel for red coalition (optional, see [Coalitions](./COALITIONS.md)).                                                                                                         |

### DCS/Hook Configuration
The DCS World integration is done via Hooks. They are being installed automatically into your configured DCS servers by the bot.

### Desanitization
DCSServerBot desanitizes your MissionScripting environment. That means, it changes entries in {DCS_INSTALLATION}\Scripts\MissionScripting.lua.
If you use any other method of desanitization, DCSServerBot checks, if additional desanitizations are needed and conducts them.
**To be able to do so, you must change the permissions on the DCS-installation directory. Give the User group write permissions for instance.**
Your MissionScripting.lua will look like this afterwards:
```lua
do
	--sanitizeModule('os')
	--sanitizeModule('io')
	--sanitizeModule('lfs')
	--_G['require'] = nil
	_G['loadlib'] = nil
	--_G['package'] = nil
end
```

### Custom MissionScripting.lua
If you want to use a **custom MissionScripting.lua** that has more sanitization (for instance for LotAtc, Moose, 
OverlordBot or the like) or additional lines to be loaded (for instance for LotAtc, or DCS-gRPC), just place the 
MissionScripting.lua of your choice in the config directory of the bot. It will be replaced on every bot startup then.

### Discord Configuration
The bot uses the following **internal** roles to apply specific permissions to commands.
You can change the role names to the ones being used in your discord. That has to be done in the dcsserverbot.ini 
configuration file. If you want to add multiple groups, separate them by comma (does **not** apply to coalition roles!).

| Role           | Description                                                                                                                                         |
|----------------|-----------------------------------------------------------------------------------------------------------------------------------------------------|
| DCS            | People with this role are allowed to chat, check their statistics and gather information about running missions and players.                        |
| DCS Admin      | People with this role are allowed to restart missions, managing the mission list, ban and unban people.                                             |
| Admin          | People with this role are allowed to manage the server, start it up, shut it down, update it, change the password and gather the server statistics. |
| GameMaster     | People with this role can see both [coalitions](./COALITIONS.md) and run specific commands that are helpful in missions.                            |
| Coalition Blue | People with this role are members of the blue coalition (see [Coalitions](./COALITIONS.md)).                                                        |
| Coalition Red  | People with this role are members of the red coalition (see [Coalitions](./COALITIONS.md)).                                                         |

### Sample Configuration
To view some sample configurations for the bot or for each configurable plugin, look [here](./config/README.md).

### Auto-Banning
The bot supports automatically bans / unbans of players from the configured DCS servers, as soon as they leave / join your Discord guild.
If you like that feature, set _AUTOBAN = true_ in dcsserverbot.ini (default = false).

However, players that are being banned from your Discord or that are being detected as hackers are auto-banned from all your configured DCS servers without prior notice.

### Additional Security Features
Players that have no pilot ID (empty) or that share an account with others, will not be able to join your DCS server. 
This is not configurable, it's a general rule (and a good one in my eyes).