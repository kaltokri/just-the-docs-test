---
has_children: true
nav_order: 4
---

# Commands

### General Administrative Commands
These commands can be used to administrate the bot itself.

| Command     | Parameter | Channel       | Role    | Description                                                                                                                                                                                                               |
|-------------|-----------|---------------|---------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| .reload     | [Plugin]  | all           | Admin   | Reloads one or all plugin(s) and their configurations from disk.                                                                                                                                                          |
| .upgrade    |           | all           | Admin   | Upgrades the bot to the latest available version (git needed, see below).                                                                                                                                                 |
| .rename     | newname   | admin-channel | Admin   | Renames a DCS server. DCSServerBot auto-detects server renaming, too.                                                                                                                                                     |
| .unregister |           | admin-channel | Admin   | Unregisters the current server from this agent.<br/>Only needed, if the very same server is going to be started on another machine connected to another agent (see "Moving a Server from one Location to Another" below). |
