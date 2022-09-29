---
title: "In-Game Commands"
weight: 3
---

**daochook** includes several custom commands that are built-in, which you can access by typing into the game chat like a normal slash command.

Commands follow the below syntax for arguments:

| Syntax | Meaning |
| --- | --- |
| `arg` | The argument is required and should be entered exactly how it's displayed. |
| `<arg>` | The argument is required, a value should be given. |
| `<arg...>` | The argument is required, one or more values should be given. |
| `(arg\|arg)` | The argument is required, one of the displayed values should be given. |
| `[arg]` | The argument is optional, a value is not required. |
| `[arg...]` | The argument is optional, one or more values are allowed. |

### Command: `/addon`

  - `/addon load <name>`
    - _Loads the an addon by its name._
  - `/addon unload <name>`
    - _Unloads an addon by its name._
  - `/addon unloadall`
    - _Unloads all currently loaded addons._
  - `/addon kill <name>`
    - _Kills an addon by its name. (Forces it to stop and unload.)_
  - `/addon reload <name>`
    - _Reloads an addon by its name._
  - `/addon exec <name> <lua_string>`
    - _Executes a string of Lua code within the given addons Lua state._
  - `/addon list`
    - _Lists the currently loaded addons._
  - `/addon info <name>`
    - _Displays information about the given addon._
  - `/addon link <name>`
    - _Opens the given addons homepage url in the systems default browser._

### Command: `/ambient`

  - `/ambient`
    - _Toggles the ambient lighting feature on or off._
  - `/ambient <0 | 1>`
    - _Sets the ambient lighting feature on or off._
  - `/ambient <r> <g> <b>`
    - _Sets the ambient lighting color._

### Command: `/fillmode`

  - `/fillmode`
    - _Toggles the fill mode feature on or off._

_This feature toggles wireframe rendering on or off._

### Command: `/fog`

  - `/fog`
    - _Toggles overriding the games fog on and off._

_This feature, when enabled, will disable the game from rendering fog._

### Command: `/zbuffer`

  - `/zbuffer`
    - _Toggles overriding the games zbuffer on and off._

_This feature, when enabled, will disable the games z-buffer rendering state._