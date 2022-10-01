---
title: "misc"
---

The `misc` namespace contains functions that don't fit into their own namespace _(either due to what they are for, or not having enough functions of the same type)_ that help with various things.

Functions exposed by this namespace are accessed via the prefix: `hook.misc.`

### Functions


#### `get_clipboard`

Returns the current string in the clipboard.

```lua
string|nil hook.misc.get_clipboard();
```

| Parameter Name | Type | Description |
| --- | --- | --- |
| _None._ | | |

| Returns |
| --- |
| _(string \| nil)_ The clipboard string on success, nil otherwise. |

---

#### `set_clipboard`

Sets the clipboard to the given string.

```lua
boolean hook.misc.set_clipboard(str);
```

| Parameter Name | Type | Description |
| --- | --- | --- |
| `str` | _string_ | The string to set the clipboard to. |

| Returns |
| --- |
| _(boolean)_ True on success, false otherwise. |

---

#### `hide_console`

Hides the debug console window.

```lua
hook.misc.hide_console();
```

| Parameter Name | Type | Description |
| --- | --- | --- |
| _None._ | | |

| Returns |
| --- |
| _None._ |

---

#### `show_console`

Shows the debug console window.

```lua
hook.misc.show_console();
```

| Parameter Name | Type | Description |
| --- | --- | --- |
| _None._ | | |

| Returns |
| --- |
| _None._ |

---

#### `execute`

Executes a program on the local machine.

```lua
hook.misc.execute(path, args, mode);
```

| Parameter Name | Type | Description |
| --- | --- | --- |
| `path` | _string_ | The path to the progam to execute. |
| `args` | _string_ | The arguments to pass to the program. |
| `mode` | _number_ | `[Optional]` The show command mode to execute the program with. |

| Returns |
| --- |
| _None._ |

---

#### `open_url`

Opens a url within the local machines default browser.

```lua
hook.misc.open_url(url);
```

| Parameter Name | Type | Description |
| --- | --- | --- |
| `url` | _string_ | The website url to open. |

| Returns |
| --- |
| _None._ |

---

#### `play_sound`

Plays a sound file. _(Plays async via PlaySoundA)_

```lua
hook.misc.play_sound(path);
```

| Parameter Name | Type | Description |
| --- | --- | --- |
| `path` | _string_ | The path to the sound file to play. |

| Returns |
| --- |
| _None._ |

_If `path` is an empty string, then any previous playing sound will be stopped._

---
