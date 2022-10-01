---
title: "extensions"
---

The `extensions` namespace is not actually a namespace that is accessible directly. Instead, this namespace is used, internally, to extend the functionality of Lua's base types. _(ie. boolean, coroutine, function, number, string, table, etc.)_

### `coroutine` Extensions

#### `kill`

Kills the current coroutine.

```lua
coroutine.kill();
```

| Parameter Name | Type | Description |
| --- | --- | --- |
| _None._ | | |

| Returns |
| --- |
| _None._ |

---

#### `sleep`

Yields the current coroutine, sleeping for the given delay of time.

```lua
coroutine.sleep(delay);
```

| Parameter Name | Type | Description |
| --- | --- | --- |
| `delay` | _number_ | The time delay to sleep for. |

| Returns |
| --- |
| _None._ |

---

#### `sleepf`

Yields the current coroutine, sleeping for the given delay of frames.

```lua
coroutine.sleepf(delay);
```

| Parameter Name | Type | Description |
| --- | --- | --- |
| `delay` | _number_ | The frame delay to sleep for. |

| Returns |
| --- |
| _None._ |

---

### `table` Extensions

#### `toliteral`

Converts the given table of numbers (bytes) to a string literal.

```lua
string table.toliteral(table);
```

| Parameter Name | Type | Description |
| --- | --- | --- |
| `table` | _table_ | The table to convert to a string literal. |

| Returns |
| --- |
| _(string)_ The converted table to a string literal. |

---
