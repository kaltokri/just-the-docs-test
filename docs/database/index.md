---
has_children: false
nav_order: 80
---

# Database
{: .no_toc }

All tables will be documented here.

1. TOC
{:toc}

## BANS

Plugin: [Admin]

| Column    | Type                             | Description                                          |
|-----------|----------------------------------|------------------------------------------------------|
| #ucid     | TEXT NOT NULL                    | Unique ID of this player. FK to the players table.   |
| banned_by | TEXT NOT NULL                    | User name that banned or DCSServerBot for auto bans. |
| reason    | TEXT                             | Reason for the ban.                                  |
| banned_at | TIMESTAMP NOT NULL DEFAULT NOW() | When was that user banned.                           |

## CAMPAIGNS

Plugin: [GameMaster]

| Column      | Type                    | Description                                     |
|-------------|-------------------------|-------------------------------------------------|
| #id         | SERIAL                  | Auto-incrementing unique ID of this campaign.   |
| name        | TEXT NOT NULL           | The campaign name.                              |
| description | TEXT                    | A brief description about the campaign.         |
| server_name | TEXT NOT NULL           | The server name the campaign is valid for.      |
| start       | TIMESTAMP DEFAULT NOW() | The start-time of the campaign (default = now). |
| stop        | TIMESTAMP               | When will the campaign stop.                    |

## COALITIONS

Plugin: [GameMaster]

| Column          | Type                    | Description                                     |
|-----------------|-------------------------|-------------------------------------------------|
| #server_name    | TEXT NOT NULL           | The respective server name.                     |
| #player_ucid    | TEXT NOT NULL           | The players UCID.                               |
| coalition       | TEXT                    | "red", "blue" or empty.                         |
| coalition_leave | TIMESTAMP               | Time when the last coalition was left.          |

## CREDITS

Plugin: [CreditSystem]

| Column       | Type                       | Description                       |
|--------------|----------------------------|-----------------------------------|
| #campaign_id | SERIAL                     | ID of this campaign.              |
| #player_ucid | TEXT NOT NULL              | The UCID of the player            |
| points       | INTEGER NOT NULL DEFAULT 0 | The earned credits of this player |

## MISSIONS

Plugin: [Mission]

| Column          | Type               | Description                                     |
|-----------------|--------------------|-------------------------------------------------|
| #id             | SERIAL             | Auto-incrementing unique mission ID.            |
| server_name     | TEXT NOT NULL      | The name of the DCS server this mission was on. |
| mission_name    | TEXT NOT NULL      | The name of the mission.                        |
| mission_theatre | TEXT NOT NULL      | The map being used by the mission.              |
| mission_start   | TIMESTAMP NOT NULL | When was this mission started.                  |
| mission_end     | TIMESTAMP          | When was this mission stopped.                  |

## MISSIONSTATS

Plugin: [MissionStats]

| Column      | Type                             | Description                                                                            |
|-------------|----------------------------------|----------------------------------------------------------------------------------------|
| #id         | SERIAL                           | Auto-incrementing unique ID of this column.                                            |
| mission_id  | INTEGER NOT NULL                 | Unique ID of this mission. FK to the missions table.                                   |
| event       | TEXT NOT NULL                    | In-game event (see list below).                                                        |
| init_id     | TEXT                             | Initiator ID, ucid of the player or -1 for AI.                                         |
| init_side   | TEXT                             | Initiator coalition, 0 = Neutral, 1 = Red, 2 = Blue                                    |
| init_type   | TEXT                             | Initiator unit type, like "FA-18c_Hornet"                                              |
| init_cat    | TEXT                             | Initiator unit category like Airplanes, Helicopters, Ships, Ground Units               |
| target_id   | TEXT                             | Target ID, ucid of the player or -1 for AI.                                            |
| target_side | TEXT                             | Target coalition, 0 = Neutral, 1 = Red, 2 = Blue                                       |
| target_type | TEXT                             | Target unit type, like "FA-18c_Hornet"                                                 |
| target_cat  | TEXT                             | Target category like Airplanes, Helicopters, Ships, Ground Units, Structure or Unknown |
| weapon      | TEXT                             | Name of the weapon. Gun if empty.                                                      |
| place       | TEXT                             | Airfield for t/o and landing events.                                                   |
| comment     | TEXT                             | Comment for LSO ratings, BDA, etc.                                                     |
| time        | TIMESTAMP NOT NULL DEFAULT NOW() | Time of the event in local time.                                                       |

## PLAYERS

Plugin: [Mission]

| Column          | Type                  | Description                                              |
|-----------------|-----------------------|----------------------------------------------------------|
| #ucid           | TEXT                  | Unique ID of this user (DCS ID).                         |
| discord_id      | BIGINT                | Discord ID of this user (if matched) or -1 otherwise.    |
| name            | TEXT                  | Last used DCS in-game-name of this user.                 |
| ipaddr          | TEXT                  | Last used IP-address of this user.                       |
| coalition       | TEXT                  | The coalition the user belongs to.                       |
| coalition_leave | TIMESTAMP             | The time that user last left their coalition.            |
| manual          | BOOLEAN DEFAULT FALSE | True if this user was manually matched, FALSE otherwise. |
| last_seen       | TIMESTAMP             | Time the user was last seen on the DCS servers.          |

## PLAYERS_HIST

Plugin: [Mission]

This table keeps a history of all changes to the main player table.

| Column     | Type                    | Description                                              |
|------------|-------------------------|----------------------------------------------------------|
| #id        | NUMBER                  | Unique ID (sequence)                                     |
| ucid       | TEXT                    | Unique ID of this user (DCS ID).                         |
| discord_id | BIGINT                  | Discord ID of this user (if matched) or -1 otherwise.    |
| name       | TEXT                    | Last used DCS in-game-name of this user.                 |
| ipaddr     | TEXT                    | Last used IP-address of this user.                       |
| coalition  | TEXT                    | The coalition the user belongs to.                       |
| manual     | BOOLEAN                 | True if this user was manually matched, FALSE otherwise. |
| time       | TIMESTAMP DEFAULT NOW() | Time of the change.                                      |

## PU_EVENTS

Plugin: [Punishment]

| Column      | Type                             | Description                                                         |
|-------------|----------------------------------|---------------------------------------------------------------------|
| #id         | SERIAL                           | Auto-incrementing unique ID of this column.                         |
| init_id     | TEXT NOT NULL                    | The initiators UCID.                                                |
| target_id   | TEXT                             | The victims UCID or -1 if AI.                                       |
| server_name | TEXT NOT NULL                    | The server name the event happened.                                 |
| event       | TEXT NOT NULL                    | The event that happened according to the configuration (see above). |
| points      | DECIMAL NOT NULL                 | The points for this event (changes during decay runs).              |
| time        | TIMESTAMP NOT NULL DEFAULT NOW() | The time the event occurred.                                        |
| decay_run   | INTEGER NOT NULL DEFAULT -1      | The decay runs that were processed on this line already.            |

## SERVERSTATS

Plugin: [ServerStats]

| Column      | Type                             | Description                                          |
|-------------|----------------------------------|------------------------------------------------------|
| #id         | SERIAL                           | Auto-incrementing unique ID of this column.          |
| agent_host  | TEXT NOT NULL                    | Hostname the bot runs on.                            |
| server_name | TEXT NOT NULL                    | Server name of this event.                           |
| mission_id  | INTEGER NOT NULL                 | The ID of the running mission.                       |
| users       | INTEGER NOT NULL                 | Number of active users at that point in time.        |
| status      | TEXT NOT NULL                    | Status of the server (PAUSED, RUNNING, etc.)         |
| cpu         | NUMERIC(5,2) NOT NULL            | CPU load of the dcs.exe process                      |
| mem_total   | NUMERIC NOT NULL                 | total memory consumption of the dcs.exe process      |
| mem_ram     | NUMERIC NOT NULL                 | part of memory being in RAM                          |
| read_bytes  | NUMERIC NOT NULL                 | number of bytes read from disk per minute            |
| write_bytes | NUMERIC NOT NULL                 | number of bytes written  to disk per minute          |
| bytes_sent  | NUMERIC NOT NULL                 | number of bytes sent over the network per minute     |
| bytes_recv  | NUMERIC NOT NULL                 | number of bytes received over the network per minute |
| fps         | NUMERIC(5,2) NOT NULL            | current "FPS" at that point in time                  |
| time        | TIMESTAMP NOT NULL DEFAULT NOW() | time of measurement                                  |

## STATISTICS

Plugin: [UserStats]

| Column             | Type                | Description                                                                                                                   |
|--------------------|---------------------|-------------------------------------------------------------------------------------------------------------------------------|
| #mission_id        | INTEGER NOT NULL    | Unique ID of this mission. FK to the missions table.                                                                          |
| #player_ucid       | TEXT NOT NULL       | Unique ID of this player. FK to the players table.                                                                            |
| #slot              | TEXT NOT NULL       | Unit type of this slot. Slots that end with "(Crew)" are sub slots in multicrew units.                                        |
| side               | INTEGER DEFAULT 0   | Side: 0 = Spectator, 1 = Red, 2 = Blue                                                                                        |
| kills              | INTEGER DEFAULT 0   | Total number of kills. Teamkills or selfkills are not counted.                                                                |
| pvp                | INTEGER DEFAULT 0   | Number of pvp-only kills. A pvp kill is a human player kill of another coalition.                                             |
| ejections          | INTEGER DEFAULT 0   | Increased when you eject. Will not be counted for multicrew atm, as there is a bug in DCS.                                    |
| crashes            | INTEGER DEFAULT 0   | Increased when your plane crashes.                                                                                            |
| teamkills          | INTEGER DEFAULT 0   | Number of FF incidents, either against players or AI.                                                                         |
| kills_planes       | INTEGER DEFAULT 0   | Increased on every kill of unit-type Airplane.                                                                                |
| kills_helicopters  | INTEGER DEFAULT 0   | Increased on every kill of unit-type Helicopter.                                                                              |
| kills_ships        | INTEGER DEFAULT 0   | Increased on every kill of unit-type Ship.                                                                                    |
| kills_sams         | INTEGER DEFAULT 0   | Increased on every kill of unit-type Air Defence.                                                                             |
| kills_ground       | INTEGER DEFAULT 0   | Increased on every kill of unit-type Ground Unit.                                                                             |
| deaths             | INTEGER DEFAULT 0   | Increased when the pilot dies. If you manage to eject and land safely, no death is counted.<br/>Teamkills don't count deaths. |
| deaths_pvp         | INTEGER DEFAULT 0   | Increased, when you die in a PVP fight (no FF).                                                                               |
| deaths_planes      | INTEGER DEFAULT 0   | Increased, when you got killed by a plane.                                                                                    |
| deaths_helicopters | INTEGER DEFAULT 0   | Increased, when you got killed by a helicopter.                                                                               |
| deaths_shops       | INTEGER DEFAULT 0   | Increased, when you got killed by a ship.                                                                                     |
| deaths_sams        | INTEGER DEFAULT 0   | Increased, when you got killed by AA.                                                                                         |
| death_ground       | INTEGER DEFAULT 0   | Increased, when you got killed by a ground unit.                                                                              |
| takeoffs           | INTEGER DEFAULT 0   | Number of takeoffs. Subsequent takeoffs inbetween one minute are counted as one takeoff (workaround DCS bug).                 |
| landings           | INTEGER DEFAULT 0   | Number of landings. Subsequent landings inbetween one minute are counted as one landing (workaround DCS bug).                 |
| #hop_on            | TIMESTAMP NOT NULL  | Time the player occupied this unit.                                                                                           |
| hop_off            | TIMESTAMP           | Time, the player left this unit or the server.                                                                                |

[Admin]: {% link plugins/admin.md %}
[CreditSystem]: {% link plugins/creditsystem.md %}
[GameMaster]: {% link plugins/gamemaster.md %}
[Mission]: {% link plugins/mission.md %}
[MissionStats]: {% link plugins/missionstats.md %}
[Punishment]: {% link plugins/punishment.md %}
[ServerStats]: {% link plugins/serverstats.md %}
[UserStats]: {% link plugins/userstats.md %}
