---
title: "extensions"
---

The `extensions` namespace is not actually a namespace that is accessible directly. Instead, this namespace is used, internally, to extend the functionality of Lua's base types. _(ie. boolean, function, number, string, table, etc.)_

### `table` Extensions

#### toliteral

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
