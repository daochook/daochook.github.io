---
title: "game"
---

The `game` namespace contains functions that **daochook** has either hooked onto, or needed to interact with from within the hook due to either the calling convention being unfriendly with FFI or similar. These are generally wrappers that are just forwarded to Lua, giving addons access to call them.

Functions exposed by this namespace are accessed via the prefix: `game.`

### Functions

#### `get_version_mode`

Returns the internal mode enumeration value that was used to read the games client version information.

{{% notice tip %}}
It is recommended that addons do no use this value as it can change without notice, and the returned value can mean something different in future updates.
{{% /notice %}}

```lua
number game.get_version_mode();
```

| Parameter Name | Type | Description |
| --- | --- | --- |
| _None._ | | |

| Returns |
| --- |
| _(number)_ The version mode enumeration value. |

The version mode values that this function can return explains what version information values should be available/populated.

  - `0` - Flags, Major, Minor1, Minor2, Revision, Build
  - `1` - Flags, Major, Minor1, Minor2
  - `2` - Major, Minor1, Minor2
  - `3` - Major, Minor1

---

#### `get_version_flags`

Returns the game clients version flags.

```lua
number game.get_version_flags();
```

| Parameter Name | Type | Description |
| --- | --- | --- |
| _None._ | | |

| Returns |
| --- |
| _(number)_ The version flags value if available, 0 otherwise. |

---

#### `get_version_major`

Returns the game clients version major value.

```lua
number game.get_version_major();
```

| Parameter Name | Type | Description |
| --- | --- | --- |
| _None._ | | |

| Returns |
| --- |
| _(number)_ The version major value if available, 0 otherwise. |

---

#### `get_version_minor1`

Returns the game clients version minor1 value.

```lua
number game.get_version_minor1();
```

| Parameter Name | Type | Description |
| --- | --- | --- |
| _None._ | | |

| Returns |
| --- |
| _(number)_ The version minor value if available, 0 otherwise. |

---

#### `get_version_minor2`

Returns the game clients version minor2 value.

```lua
number game.get_version_minor2();
```

| Parameter Name | Type | Description |
| --- | --- | --- |
| _None._ | | |

| Returns |
| --- |
| _(number)_ The version minor value if available, 0 otherwise. |

---

#### `get_version_revision`

Returns the game clients version revision value.

```lua
number game.get_version_revision();
```

| Parameter Name | Type | Description |
| --- | --- | --- |
| _None._ | | |

| Returns |
| --- |
| _(number)_ The version revision value if available, 0 otherwise. |

---

#### `get_version_build`

Returns the game clients version build value.

```lua
number game.get_version_build();
```

| Parameter Name | Type | Description |
| --- | --- | --- |
| _None._ | | |

| Returns |
| --- |
| _(number)_ The version build value if available, 0 otherwise. |

---

#### `get_version_id`

Returns the **daochook** internal version id specifier.

{{% notice tip %}}
It is recommended that addons do no use this value as it can change without notice, and the returned value can mean something different in future updates.
{{% /notice %}}

```lua
number game.get_version_id();
```

| Parameter Name | Type | Description |
| --- | --- | --- |
| _None._ | | |

| Returns |
| --- |
| _(number)_ The version id enumeration value. |

The list of values that this function can return are not intended for use by addons. Therefore the list will not be shared publicly. This value is used internally by **daochook** to tell what client version is running. Addons can determine that information by using the various other `get_version_xxx` functions. The values this function returns are subject to change without warning, it is not recommended to rely on this function in your addons.

---

#### `get_game_state`

Returns the game state pointer.

```lua
number game.get_game_state();
```

| Parameter Name | Type | Description |
| --- | --- | --- |
| _None._ | | |

| Returns |
| --- |
| _(number)_ The game state pointer if valid, 0 otherwise. |

---

#### `get_global_value`

Calls a game function that is used to get a global numerical value.

```lua
number game.get_global_value(index);
```

| Parameter Name | Type | Description |
| --- | --- | --- |
| `index` | _number_ | The value index to return. |

| Returns |
| --- |
| _(number)_ The global numerical value at the given index. |

---

#### `get_entity_index_by_objectid`

Calls a game function that is used to get an entity index by its object id.

```lua
number game.get_entity_index_by_objectid(object_id);
```

| Parameter Name | Type | Description |
| --- | --- | --- |
| `object_id` | _number_ | The entity object id to obtain the index of. |

| Returns |
| --- |
| _(number)_ The entity index on success, -1 otherwise. |

---

#### `get_entity_string`

Calls a game function that is used to return an entity related string.

```lua
string game.get_entity_string(table_index, entity_index);
```

| Parameter Name | Type | Description |
| --- | --- | --- |
| `table_index`     | _number_ | The table index of the string to obtain. |
| `entity_index`    | _number_ | The entity index to obtain the string for. |

| Returns |
| --- |
| _(string)_ The entity string. |

The table index values are:

  - `0` - String table that contains entity titles.
  - `1` - Unknown.
  - `2` - Unknown.
  - `3` - String table that contains entity names.
  - `4` - Unknown.

---

#### `exec_command`

Calls the games input command handler, executing the given command.

```lua
game.exec_command(mode, imode, command);
```

| Parameter Name | Type | Description |
| --- | --- | --- |
| `mode`    | _number_ | The command mode. |
| `imode`   | _number_ | The command input mode. |
| `command` | _string_ | The command string. |

| Returns |
| --- |
| _None._ |

The command mode values are:

  - `0` - The command should be executed as player input.
  - `1` - The command should be executed as a macro.
  - `2` - The command should be executed as the client/system.

The command input mode values are:

  - `0` - The command should be executed as if it was started by pressing `Enter`.
  - `1` - The command should be executed as if it was started by pressing `/`.
  - `2` - The command should be executed as if it was started by pressing `]`.

---

#### `add_message`

Calls the games output message handler, printing the given message to the chat/combat log(s).

```lua
game.add_message(mode, message);
```

| Parameter Name | Type | Description |
| --- | --- | --- |
| `mode`    | _number_ | The message mode. |
| `message` | _string_ | The message string. |

| Returns |
| --- |
| _None._ |

---

#### `recv_packet`

Calls the games packet handler function, sending the given packet to the client as if the server sent it.

```lua
game.recv_packet(opcode, packet);
```

| Parameter Name | Type | Description |
| --- | --- | --- |
| `opcode` | _number_   | The packet opcode. |
| `packet` | _table_    | The packet data, as a table of bytes. |

| Returns |
| --- |
| _None._ |

---

#### `send_packet`

Calls the games packet send function, sending the given packet to the server as if the client sent it.

```lua
game.send_packet(opcode, packet, parameter);
```

| Parameter Name | Type | Description |
| --- | --- | --- |
| `opcode`      | _number_  | The packet opcode. |
| `packet`      | _table_   | The packet data, as a table of bytes. |
| `parameter`   | _number_  | The packet parameter. |

| Returns |
| --- |
| _None._ |

---
