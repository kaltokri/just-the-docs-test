---
title: PostgreSQL
parent: Installation
---

DCSServerBot uses [PostgreSQL] to store all information that needs to be persisted, like players, mission information, statistics and so on.
Therefor, it needs a fast database. Starting with SQLite back in the days, I decided to move over to [PostgreSQL] and never regret it.

{: .note }
> If you don't want to install and maintain a [PostgreSQL] server, take a look at [DCSServerBotLight], which doesn't need a PostgreSQL-database, but has a limited feature set.

Just download and install [PostgreSQL] from the website (current version at the time of writing is 14, but will run with any newer version than that, too).
Or you can use a package manager of your choice [Winget] / [Chocolaty]:
- `choco install postgresql`
- `winget install postgresql`

The install wizzard of DCSServerBot will recognize a local installed [PostgreSQL] automatically and use it.
You just give it the postgres user and password and it will create the database and a user for you.

# Remote database server

It is possible to use an already existing databse server on another machine. But you need to create the database `dcsserverbot` and user `dcsserverbot` manually.
Configure the needed option `DATABASE_URL` in the `dcsserverbot.ini`. On startup the bot will create all tables that are needed.

{: .warning }
> The installation wizzard aborts the installation if it is unable to find a local database. You have to configure the bot manually until this bug is fixed.

{: .important }
> If using PostgreSQL remotely over unsecured networks, it is recommended to have SSL enabled.

[DCSServerBotLight]: https://github.com/Special-K-s-Flightsim-Bots/DCSServerBotLight
[PostgreSQL]: https://www.postgresql.org/
