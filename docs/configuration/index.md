---
has_children: true
nav_order: 3
---

# Configuration

The configuration of DcsServerBot is done in the file `dcsserverbot.ini`.
You will find a describtion for all settings in the subsection.

The bot must disable some security settings of your DCS server. See details under Desanitization.

A special feature is the coalition mode. Read details about it here in the matching subsection.

## Sample Configuration
To view some sample configurations for the bot or for each configurable plugin, look [here](./config/README.md).

## DCS Hook Configuration
The DCS World integration is done via Hooks. They are being installed automatically into your configured DCS servers by the bot.

### Auto-Banning
The bot supports automatically bans / unbans of players from the configured DCS servers, as soon as they leave / join your Discord guild.
If you like that feature, set _AUTOBAN = true_ in dcsserverbot.ini (default = false).

However, players that are being banned from your Discord or that are being detected as hackers are auto-banned from all your configured DCS servers without prior notice.

### Additional Security Features
Players that have no pilot ID (empty) or that share an account with others, will not be able to join your DCS server. 
This is not configurable, it's a general rule (and a good one in my eyes).
