---
title: "daoc"
---

The `daoc` _(Dark Age of Camelot)_ library is used to add game related functionality and information. The main library file will automatically determine your client version, then include the additional version-specific sub-library files found within the `/addons/libs/daoc/` folder. These sub folders are separate into client versions to ensure that the functionality will work on as many clients as possible. It’s also easy to add support for other client versions by simply making a copy of an existing folder and updating the function information and pointers appropriately.

This library makes heavy use of LuaJIT's FFI library, which allows Lua to be able to define C-style structures as well as cast to and allocate against C-style functions and memory. This allows Lua to directly call game functions, query for the game structures as they are in memory, etc. Please note that because of how this library works, it is more prone to hard-crashing the client if you are not careful with how you attempt to use things. You should always check returns for nil when appropriate before attempting to make use of a returned structure/object or function call.

### Using The Library

```lua
require 'daoc';
```

### Functions

This library implements a series of _(automatically included)_ sub-libraries which each contain a set of functions and enumerations. This library is still being developed and thus documentation will not be posted here at this time. Please refer to the individual files for more information on the functions and enumerations they expose.

| Sub-Library Name | Functionality |
| --- | --- |
| `buffs`   | Exposes functions related to querying the players buffs and buff related timers. |
| `chat`    | Exposes functions and enumerations related to interacting with the games chat windows and command input handler. |
| `data`    | Exposes functions related to game data. _(ie. spells pulled from `spells.csv`)_ |
| `entities`| Exposes functions and enumerations related to entities and similar objects. |
| `game`    | Exposes functions related to game specific functionality not currently part of other sub-libraries. _(ie. calling packet send functions)_ |
| `items`   | Exposes functions and enumerations related to the players various inventory and item slots along with money.. |
| `main`    | Sub-library module that includes the other libraries listed here in a single require. |
| `party`   | Exposes functions and enumerations related to the local players party members. |
| `player`  | Exposes functions and enumerations related to the local player. |
| `states`  | Exposes functions and enumerations related to various game state objects. |
