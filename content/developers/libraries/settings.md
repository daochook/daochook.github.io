---
title: "settings"
---

The `settings` library is used to allow addons to create per-character configuration files. The library manages and handles the switching of characters automatically, addons simply need to register to an event, per-settings block, to receive the updated settings table information when a character switch happens.

_Settings are serialized into a readable Lua table format making it easy for users to modify the settings on disk if needed._

The library will default to a character alias of `_default_` when no character is logged in. Most of the functions of this library that accept an alias consider the alias optional. When no alias is given to these functions, then a default alias of `settings` is used instead.

The settings files are saved to the **daochook** configurations folder. These are saved within this folder under a series of subfolders. For example:

  - **Defaults:** `<daochook_path>/config/addons/<addon_name>/_defaults_/<alias>.lua`
  - **Character:** `<daochook_path>/config/addons/<addon_name>/<character_name>/<alias>.lua`

An example set of paths would be the following for the `fps` addon:

  - **Defaults:** `<daochook_path>/config/addons/fps/_defaults_/settings.lua`
  - **Character:** `<daochook_path>/config/addons/fps/Atomos/settings.lua`

### Using The Library

```lua
local settings = require 'settings';
```

### Functions

#### `settings_path`

Returns the current settings path. (Specific to the given addons namespace.)

```lua
string settings.settings_path();
```

| Parameter Name | Type | Description |
| --- | --- | --- |
| _None._ | | |

| Returns |
| --- |
| _(string)_ The settings path for the current addon. |

The path returned by this function will look like this:

  - When logged out: `<daochook_path>/config/addons/<addon_name>/_defaults_/`
  - When logged in: `<daochook_path>/config/addons/<addon_name>/<character_name>/`

---

#### `load`

Loads and returns a settings table.

```lua
table settings.load(defaults);
table settings.load(defaults, alias);
```

| Parameter Name | Type | Description |
| --- | --- | --- |
| `defaults`    | _table_   | The default settings table to be used if no settings are loaded from disk. |
| `alias`       | _string_  | `[Optional]` The alias to store the settings within. |

| Returns |
| --- |
| _(table)_ The settings table. |

If no alias is given, then the default alias of `settings` will be used instead.

_**Note:** This function will raise events against the `alias`._

___

#### `save`

Saves a settings table to disk.

```lua
boolean settings.save();
boolean settings.save(alias);
```

| Parameter Name | Type | Description |
| --- | --- | --- |
| `alias` | _string_  | `[Optional]` The alias of the settings to save. |

| Returns |
| --- |
| _(boolean)_ True on success, false otherwise. |

If no alias is given, then the default alias of `settings` will be used instead.

___

#### `reload`

Reloads a settings table from disk.

```lua
boolean settings.reload();
boolean settings.reload(alias);
```

| Parameter Name | Type | Description |
| --- | --- | --- |
| `alias` | _string_  | `[Optional]` The alias of the settings to reload. |

| Returns |
| --- |
| _(boolean)_ True on success, false otherwise. |

If no alias is given, then the default alias of `settings` will be used instead.

_**Note:** This function will raise events against the `alias`._

---

#### `reset`

Resets a settings table to its defaults.

```lua
boolean settings.reset();
boolean settings.reset(alias);
```

| Parameter Name | Type | Description |
| --- | --- | --- |
| `alias` | _string_  | `[Optional]` The alias of the settings to reset. |

| Returns |
| --- |
| _(boolean)_ True on success, false otherwise. |

If no alias is given, then the default alias of `settings` will be used instead.

_**Note:** This function will raise events against the `alias`._

---

#### `get`

Returns the settings table for the given alias.

```lua
table|nil settings.get();
table|nil settings.get(alias);
```

| Parameter Name | Type | Description |
| --- | --- | --- |
| `alias` | _string_  | `[Optional]` The alias of the settings to get. |

| Returns |
| --- |
| _(table \| nil)_ The settings table on success, nil otherwise. |

If no alias is given, then the default alias of `settings` will be used instead.

---

#### `register`

Registers an event callback to a settings block.

```lua
settings.register(alias, event_alias, callback);
```

| Parameter Name | Type | Description |
| --- | --- | --- |
| `alias`       | _string_      | The alias of the settings block to register the event for. |
| `event_alias` | _string_      | The alias of the event callback. _(Must be unique per-alias.)_ |
| `callback`    | _function_    | The callback function to invoke when a settings event is raised. |

| Returns |
| --- |
| _None._ |

---

#### `unregister`

Unregisters an event callback from a settings block.

```lua
settings.unregister(alias, event_alias);
```

| Parameter Name | Type | Description |
| --- | --- | --- |
| `alias`       | _string_      | The alias of the settings block to unregister the event for. |
| `event_alias` | _string_      | The alias of the event callback. |

| Returns |
| --- |
| _None._ |

---

#### `process`

Processes a settings table, converting it to a string that can be reloaded into Lua later.

```lua
string settings.process(o, space);
```

| Parameter Name | Type | Description |
| --- | --- | --- |
| `o`       | _any_     | The object to process. _(Generally a table to begin.)_ |
| `space`   | _string_  | `[Optional]` The indent spacing to use. _(Default is 4 spaces.)_ |

| Returns |
| --- |
| _(string)_ The processed string of the given `o` data. |

---

### Event Usage

The `settings` library makes use of a custom event setup _(similar to normal addon events)_ that is used to inform an addon of when a settings table is changed. _(Via loading, reload, or resetting.)_ Addons can register to a specific settings table for this event to ensure their current settings are up to date with what the library has currently loaded and cached.

The registration to the given event looks like this:

```lua
settings.register('settings', 'settings_update', function (e)

end);
```

_**Note:** The alias given here, `settings` is the default alias when a unique one is not given. If you are using a specific alias for your settings, then you should change this string to match!_

When this event is invoked, `e` will contain the updated settings table that your addon should make use of. It is also ideal for your addon to make any adjustments, update its various properties/UI/etc. and such in relation to these new settings to ensure what is curerntly being shown/used is properly up to date. Afterward, it is suggested that you also save the settings after to ensure your settings and the library match on disk.

Here is an example of all of this:

```lua
-- Include the needed libraries..
require 'common';
local settings = require 'settings';

-- Define your addons default settings..
local default_settings = T{
    value1 = 1234,
    value2 = true,
    value3 = 'Hello world.',
};

-- Load the addon settings..
local cfg = settings.load(default_settings);

-- Register to the settings update event..
settings.register('settings', 'settings_update', function (e)
    -- Update the settings table..
    cfg = e;

    --[[
    Do additional updates to your addons properties here.
    --]]

    -- Ensure settings are saved to disk when changed..
    settings.save();
end);
```

You should not edit your `default_settings` table ever when defining it as the defauls/outline of what you expect for your addons settings. All edits should be made to the table returned from `settings.load(...)`. If you need to obtain the settings table again you can use `settings.get(...)` to obtain the table from the settings library.

