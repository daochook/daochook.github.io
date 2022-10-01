---
title: "hook"
---

The `hook` namespace contains functions that directly interact with **daochook**.

Functions exposed by this namespace are accessed via the prefix: `hook.`

### Functions

#### `get_hook_path`

Returns the path to where **daochook** is installed.

```lua
string hook.get_hook_path();
```

| Parameter Name | Type | Description |
| --- | --- | --- |
| _None._ | | |

| Returns |
| --- |
| _(string)_ The path where **daochook** is installed. |

---

#### `get_hook_base`

Returns the base address of **daochook** in the current process.

```lua
number hook.get_hook_base();
```

| Parameter Name | Type | Description |
| --- | --- | --- |
| _None._ | | |

| Returns |
| --- |
| _(number)_ The base address of **daochook** in the current process. |

---

#### `get_game_path`

Returns the path to where the game client is installed.

```lua
string hook.get_game_path();
```

| Parameter Name | Type | Description |
| --- | --- | --- |
| _None._ | | |

| Returns |
| --- |
| _(string)_ The path where the game client is installed. |

---

#### `get_game_base`

Returns the base address of `game.dll` in the current process.

```lua
number hook.get_game_base();
```

| Parameter Name | Type | Description |
| --- | --- | --- |
| _None._ | | |

| Returns |
| --- |
| _(number)_ The base address of the `game.dll` module in the current process. |

---

#### `get_game_size`

Returns the size of the `game.dll` module.

```lua
number hook.get_game_size();
```

| Parameter Name | Type | Description |
| --- | --- | --- |
| _None._ | | |

| Returns |
| --- |
| _(number)_ The size of the `game.dll` module. |

---

#### `get_game_hwnd`

Returns the window handle of the main game window.

```lua
number hook.get_game_hwnd();
```

| Parameter Name | Type | Description |
| --- | --- | --- |
| _None._ | | |

| Returns |
| --- |
| _(number)_ The window handle of main game window. |

---

#### `get_d3d9`

Returns the games `IDirect3D9*` device pointer.

```lua
userdata hook.get_d3d9();
```

| Parameter Name | Type | Description |
| --- | --- | --- |
| _None._ | | |

| Returns |
| --- |
| _(userdata)_ The games `IDirect3D9*` device pointer. |

---

#### `get_d3d9dev`

Returns the games `IDirect3DDevice9*` device pointer.

```lua
userdata hook.get_d3d9dev();
```

| Parameter Name | Type | Description |
| --- | --- | --- |
| _None._ | | |

| Returns |
| --- |
| _(userdata)_ The games `IDirect3DDevice9*` device pointer. |

---

#### `get_use_ambient_override`

Returns the current state of the ambient override feature.

```lua
boolean hook.get_use_ambient_override();
```

| Parameter Name | Type | Description |
| --- | --- | --- |
| _None._ | | |

| Returns |
| --- |
| _(boolean)_ The current state of the feature. |

---

#### `set_use_ambient_override`

Sets the ambient override feature on or off.

```lua
hook.set_use_ambient_override(flag);
```

| Parameter Name | Type | Description |
| --- | --- | --- |
| `flag` | _boolean_ | Flag that states if the feature should be enabled or disabled. |

| Returns |
| --- |
| _None._ |

---

#### `get_ambient_color`

Returns the ambient color override value.

```lua
number hook.get_ambient_color();
```

| Parameter Name | Type | Description |
| --- | --- | --- |
| _None._ | | |

| Returns |
| --- |
| _(number)_ The ambient color that will be used when the feature is enabled. |

---

#### `set_ambient_color`

Sets the ambient color value to be used when the ambient color override feature is enabled.

```lua
hook.set_ambient_color(r, g, b);
```

| Parameter Name | Type | Description |
| --- | --- | --- |
| `r` | _number_ | The red color amount. _(0 to 255)_ |
| `g` | _number_ | The green color amount. _(0 to 255)_ |
| `b` | _number_ | The blue color amount. _(0 to 255)_ |

| Returns |
| --- |
| _None._ |

---

#### `get_use_fillmode_override`

Returns the current state of the fillmode override feature.

```lua
boolean hook.get_use_fillmode_override();
```

| Parameter Name | Type | Description |
| --- | --- | --- |
| _None._ | | |

| Returns |
| --- |
| _(boolean)_ The current state of the feature. |

---

#### `set_use_fillmode_override`

Sets the fillmode override feature on or off.

```lua
hook.set_use_fillmode_override(flag);
```

| Parameter Name | Type | Description |
| --- | --- | --- |
| `flag` | _boolean_ | Flag that states if the feature should be enabled or disabled. |

| Returns |
| --- |
| _None._ |

---

#### `get_use_fog_override`

Returns the current state of the fog override feature.

```lua
boolean hook.get_use_fog_override();
```

| Parameter Name | Type | Description |
| --- | --- | --- |
| _None._ | | |

| Returns |
| --- |
| _(boolean)_ The current state of the feature. |

---

#### `set_use_fog_override`

Sets the fog override feature on or off.

```lua
hook.set_use_fog_override(flag);
```

| Parameter Name | Type | Description |
| --- | --- | --- |
| `flag` | _boolean_ | Flag that states if the feature should be enabled or disabled. |

| Returns |
| --- |
| _None._ |

---

#### `get_use_zbuffer_override`

Returns the current state of the zbuffer override feature.

```lua
boolean hook.get_use_zbuffer_override();
```

| Parameter Name | Type | Description |
| --- | --- | --- |
| _None._ | | |

| Returns |
| --- |
| _(boolean)_ The current state of the feature. |

---

#### `set_use_zbuffer_override`

Sets the zbuffer override feature on or off.

```lua
hook.set_use_zbuffer_override(flag);
```

| Parameter Name | Type | Description |
| --- | --- | --- |
| `flag` | _boolean_ | Flag that states if the feature should be enabled or disabled. |

| Returns |
| --- |
| _None._ |

---

### Configuration Manager

Functions exposed for this manager are accessed via the prefix: `hook.cfg.`

#### `load`

Loads a configuration file into the cache.

```lua
boolean hook.cfg.load(alias, file);
```

| Parameter Name | Type | Description |
| --- | --- | --- |
| `alias`   | _string_ | The configuration cache alias. |
| `file`    | _string_ | The file path to the configurations. |

| Returns |
| --- |
| _(boolean)_ True on success, false otherwise. |

---

#### `save`

Saves a configuration cache block to a file.

```lua
boolean hook.cfg.save(alias);
boolean hook.cfg.save(alias, file);
```

| Parameter Name | Type | Description |
| --- | --- | --- |
| `alias`   | _string_ | The configuration cache alias. |
| `file`    | _string_ | `[Optional]` The override file path to save the configurations to. |

| Returns |
| --- |
| _(boolean)_ True on success, false otherwise. |

---

#### `remove`

Removes a configuration block from the cache.

```lua
hook.cfg.remove(alias);
```

| Parameter Name | Type | Description |
| --- | --- | --- |
| `alias`   | _string_ | The alias of the configuration cache to remove. |

| Returns |
| --- |
| _None._ |

---

#### `get_sections`

Returns the sections within a configuration block.

```lua
string|nil hook.cfg.get_sections(alias);
```

| Parameter Name | Type | Description |
| --- | --- | --- |
| `alias` | _string_ | The configuration cache alias. |

| Returns |
| --- |
| _(string \| nil)_ String containing the section names on success, nil otherwise. |

---

#### `get_section_keys`

Returns the section keys within a configuration section.

```lua
string|nil hook.cfg.get_section_keys(alias, section);
```

| Parameter Name | Type | Description |
| --- | --- | --- |
| `alias`   | _string_ | The configuration cache alias. |
| `section` | _string_ | The configuration section name. |

| Returns |
| --- |
| _(string \| nil)_ String containing the section keys on success, nil otherwise. |

---

#### `get_string`

Returns a string value from a configuration.

```lua
string|nil hook.cfg.get_string(alias, section, key);
```

| Parameter Name | Type | Description |
| --- | --- | --- |
| `alias`   | _string_ | The configuration cache alias. |
| `section` | _string_ | The configuration section name. |
| `key`     | _string_ | The configuration key. |

| Returns |
| --- |
| _(string)_ The configuration value on success, nil otherwise. |

---

#### `set_value`

Sets a configuration value.

```lua
hook.cfg.set_value(alias, section, key, value);
```

| Parameter Name | Type | Description |
| --- | --- | --- |
| `alias`   | _string_ | The configuration cache alias. |
| `section` | _string_ | The configuration section name. |
| `key`     | _string_ | The configuration key. |
| `value`   | _string_ | The value to set. |

| Returns |
| --- |
| _None._ |

---

#### `get_values`

Returns a configuration files values.

```lua
table|nil hook.cfg.get_values(alias);
```

| Parameter Name | Type | Description |
| --- | --- | --- |
| `alias` | _string_ | The configuration cache alias. |

| Returns |
| --- |
| _(table \| nil)_ Table containing the entire configuration file information on success, nil otherwise. |

---

#### `get_bool`

Returns a configuration value _(bool)_

```lua
boolean hook.cfg.get_bool(alias, section, key, default_value);
```

| Parameter Name | Type | Description |
| --- | --- | --- |
| `alias`           | _string_  | The configuration cache alias. |
| `section`         | _string_  | The section that owns the desired value. |
| `key`             | _string_  | The key of the value to obtain. |
| `default_value`   | _boolean_ | The default value to use if the given key does not exist. |

| Returns |
| --- |
| _(boolean)_ The configuration value on success, `default_value` otherwise. |

---

#### `get_uint8`

Returns a configuration value _(uint8)_

```lua
number hook.cfg.get_uint8(alias, section, key, default_value);
```

| Parameter Name | Type | Description |
| --- | --- | --- |
| `alias`           | _string_  | The configuration cache alias. |
| `section`         | _string_  | The section that owns the desired value. |
| `key`             | _string_  | The key of the value to obtain. |
| `default_value`   | _number_  | The default value to use if the given key does not exist. |

| Returns |
| --- |
| _(number)_ The configuration value on success, `default_value` otherwise. |

---

#### `get_uint16`

Returns a configuration value _(uint16)_

```lua
number hook.cfg.get_uint16(alias, section, key, default_value);
```

| Parameter Name | Type | Description |
| --- | --- | --- |
| `alias`           | _string_  | The configuration cache alias. |
| `section`         | _string_  | The section that owns the desired value. |
| `key`             | _string_  | The key of the value to obtain. |
| `default_value`   | _number_  | The default value to use if the given key does not exist. |

| Returns |
| --- |
| _(number)_ The configuration value on success, `default_value` otherwise. |

---

#### `get_uint32`

Returns a configuration value _(uint32)_

```lua
number hook.cfg.get_uint32(alias, section, key, default_value);
```

| Parameter Name | Type | Description |
| --- | --- | --- |
| `alias`           | _string_  | The configuration cache alias. |
| `section`         | _string_  | The section that owns the desired value. |
| `key`             | _string_  | The key of the value to obtain. |
| `default_value`   | _number_  | The default value to use if the given key does not exist. |

| Returns |
| --- |
| _(number)_ The configuration value on success, `default_value` otherwise. |

---

#### `get_uint64`

Returns a configuration value _(uint64)_

```lua
number hook.cfg.get_uint64(alias, section, key, default_value);
```

| Parameter Name | Type | Description |
| --- | --- | --- |
| `alias`           | _string_  | The configuration cache alias. |
| `section`         | _string_  | The section that owns the desired value. |
| `key`             | _string_  | The key of the value to obtain. |
| `default_value`   | _number_  | The default value to use if the given key does not exist. |

| Returns |
| --- |
| _(number)_ The configuration value on success, `default_value` otherwise. |

---

#### `get_int8`

Returns a configuration value _(int8)_

```lua
number hook.cfg.get_int8(alias, section, key, default_value);
```

| Parameter Name | Type | Description |
| --- | --- | --- |
| `alias`           | _string_  | The configuration cache alias. |
| `section`         | _string_  | The section that owns the desired value. |
| `key`             | _string_  | The key of the value to obtain. |
| `default_value`   | _number_  | The default value to use if the given key does not exist. |

| Returns |
| --- |
| _(number)_ The configuration value on success, `default_value` otherwise. |

---

#### `get_int16`

Returns a configuration value _(int16)_

```lua
number hook.cfg.get_int16(alias, section, key, default_value);
```

| Parameter Name | Type | Description |
| --- | --- | --- |
| `alias`           | _string_  | The configuration cache alias. |
| `section`         | _string_  | The section that owns the desired value. |
| `key`             | _string_  | The key of the value to obtain. |
| `default_value`   | _number_  | The default value to use if the given key does not exist. |

| Returns |
| --- |
| _(number)_ The configuration value on success, `default_value` otherwise. |

---

#### `get_int32`

Returns a configuration value _(int32)_

```lua
number hook.cfg.get_int32(alias, section, key, default_value);
```

| Parameter Name | Type | Description |
| --- | --- | --- |
| `alias`           | _string_  | The configuration cache alias. |
| `section`         | _string_  | The section that owns the desired value. |
| `key`             | _string_  | The key of the value to obtain. |
| `default_value`   | _number_  | The default value to use if the given key does not exist. |

| Returns |
| --- |
| _(number)_ The configuration value on success, `default_value` otherwise. |

---

#### `get_int64`

Returns a configuration value _(int64)_

```lua
number hook.cfg.get_int64(alias, section, key, default_value);
```

| Parameter Name | Type | Description |
| --- | --- | --- |
| `alias`           | _string_  | The configuration cache alias. |
| `section`         | _string_  | The section that owns the desired value. |
| `key`             | _string_  | The key of the value to obtain. |
| `default_value`   | _number_  | The default value to use if the given key does not exist. |

| Returns |
| --- |
| _(number)_ The configuration value on success, `default_value` otherwise. |

---

#### `get_float`

Returns a configuration value _(float)_

```lua
number hook.cfg.get_float(alias, section, key, default_value);
```

| Parameter Name | Type | Description |
| --- | --- | --- |
| `alias`           | _string_  | The configuration cache alias. |
| `section`         | _string_  | The section that owns the desired value. |
| `key`             | _string_  | The key of the value to obtain. |
| `default_value`   | _number_  | The default value to use if the given key does not exist. |

| Returns |
| --- |
| _(number)_ The configuration value on success, `default_value` otherwise. |

---

#### `get_double`

Returns a configuration value _(double)_

```lua
number hook.cfg.get_double(alias, section, key, default_value);
```

| Parameter Name | Type | Description |
| --- | --- | --- |
| `alias`           | _string_  | The configuration cache alias. |
| `section`         | _string_  | The section that owns the desired value. |
| `key`             | _string_  | The key of the value to obtain. |
| `default_value`   | _number_  | The default value to use if the given key does not exist. |

| Returns |
| --- |
| _(number)_ The configuration value on success, `default_value` otherwise. |

---

### Pointer Manager

Functions exposed for this manager are accessed via the prefix: `hook.pointers.`

#### `load`

Loads a file that contains pointer related configurations into the pointer cache.

```lua
boolean hook.pointers.load(file);
```

| Parameter Name | Type | Description |
| --- | --- | --- |
| `file`    | _string_ | The file path to the configurations. |

| Returns |
| --- |
| _(boolean)_ True on success, false otherwise. |

---

#### `add`

Adds a pointer to the pointer cache.

```lua
number hook.pointers.add(name, pointer);
```

| Parameter Name | Type | Description |
| --- | --- | --- |
| `name`    | _string_ | The name of the pointer. |
| `pointer` | _number_ | The existing pointer value. |

| Returns |
| --- |
| _(number)_ The pointer value passed in `pointer`. |

```lua
number hook.pointers.add(name, module_name, pattern, offset, count);
```

| Parameter Name | Type | Description |
| --- | --- | --- |
| `name`        | _string_ | The name of the pointer. |
| `module_name` | _string_ | The name of the module to scan for the pointer within. |
| `pattern`     | _string_ | The pattern of data to scan for. |
| `offset`      | _number_ | The offset to add to the address where the pattern was found. |
| `count`       | _number_ | The count of the result to use if the pattern is found more than once. |

| Returns |
| --- |
| _(number)_ The pointer value passed in `pointer`. |

---

#### `get`

Returns a pointer from the pointer cache.

```lua
number hook.pointers.get(name);
```

| Parameter Name | Type | Description |
| --- | --- | --- |
| `name` | _string_ | The name of the pointer. |

| Returns |
| --- |
| _(number)_ The pointer value if valid, 0 otherwise. |

---
