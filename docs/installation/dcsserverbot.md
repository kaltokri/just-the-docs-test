---
title: DcsServerBot
parent: Installation
nav_order: 6
---

# Download

Best is to use git clone https://github.com/Special-K-s-Flightsim-Bots/DCSServerBot.git as you then can use the autoupdate functionality of the bot.
Otherwise download the latest release version and extract it somewhere on your PC that is running the DCS server(s) and give it write permissions, if needed.

Attention: Make sure that the bots installation directory can only be seen by yourself and is not exposed to anybody outside via www etc.

# Installation

Just run the provided install script. It will search for existing DCS installations, create a database user and database and asks you to add existing DCS servers to the configuration file (see below).

# DCS/Hook Configuration

The DCS World integration is done via Hooks. They are being installed automatically into your configured DCS servers by the bot.
