---
title: Desanitization
parent: Configuration
nav_order: 2
---

# Desanitization

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