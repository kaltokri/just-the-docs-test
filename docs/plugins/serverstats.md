---
title: ServerStats
parent: Plugin System
nav_order: 0
---

# Plugin "ServerStats"

If you enable this plugin you will gather statistics for your DCS servers.<br/>

## Configuration

n/a

## Discord Commands

| Command      | Parameter               | Role  | Description                                                                                                                                             |
|--------------|-------------------------|-------|---------------------------------------------------------------------------------------------------------------------------------------------------------|
| .serverstats | [day/week/month] [-all] | Admin | Displays server statistics, like usual playtime, most frequented servers and missions.<br/>If -all is provided, you can cycle through all your servers. |
| .serverload  | [hour/day/week] [-all]  | Admin | Displays technical server statistics, like CPU load, memory consumption, etc.<br/>If -all is provided, you can cycle through all your server nodes.     |

## Database Tables

{% capture link_with_anchor %}{% link database/index.md %}#serverstats{% endcapture %}
- [SERVERSTATS]({{ link_with_anchor }})
