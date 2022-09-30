---
title: "Addon Table Information"
pre: "2. "
weight: 2
---

The `addon` table is predefined within **daochook** for each addon being loaded. This table contains some additional properties that can be used/accessed by an addon while it's running.

{{% notice warning %}}
You should **NEVER** attempt to recreate the `addon` table or set it to a new value!\
This will cause your addon to crash and potentially crash the full client.
{{% /notice %}}

### `addon` Table Information

The following table is the properties available within the `addon` table.

| Field | Type | Description |
| --- | --- | --- |
| `author`          | _string_      | The name of the author who wrote the addon. |
| `desc`            | _string_      | Short description of what the addon does / is for. |
| `instance`        | _userdata_    | `[Read Only]` The internal addon object pointer. _(See below for more info.)_ |
| `link`            | _string_      | The url to the addons homepage, where users can find information, support, or updates. |
| `name`            | _string_      | The name of the addon. |
| `path`            | _string_      | `[Read Only]` The path to the addon. |
| `tasks`           | _table_       | `[Read Only]` Internal table that holds running task coroutine information. |
| `version`         | _string_      | The version of the addon. _(In the format of X.X.X, such as 1.0.0)_ |

The `addon.instance` object exposes a few properties that addons can use to check certain information.

| Field | Type | Description |
| --- | --- | --- |
| `current_frame`   | _number_      | `[Read Only]` The current frame count the addon is executing on. |
| `state`           | _number_      | `[Read Only]` The addons current state. |

_**Note:** Attempting to write to any read-only value will cause your addon to error and unload._