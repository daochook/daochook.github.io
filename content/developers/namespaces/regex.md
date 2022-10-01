---
title: "regex"
---

The `regex` namespace contains functions that allow for more advanced regular expression usage.

{{% notice tip %}}
These file system functions make use of the C++ `std::regex` header. The functions are named the same/similar.\
For more information on those functions, please visit: https://en.cppreference.com/w/cpp/regex
{{% /notice %}}

Functions exposed by this namespace are accessed via the prefix: `hook.regex.`

### Functions

#### `match`

Returns any matches to the given pattern on the given string. _(Uses std::regex\_match)_

```lua
table|nil hook.regex.match(message, pattern, flags);
```

| Parameter Name | Type | Description |
| --- | --- | --- |
| `message` | _string_ | The message to match the pattern within. |
| `pattern` | _string_ | The pattern to match. |
| `flags`   | _number_ | `[Optional]` The regex flags to use while matching. |

| Returns |
| --- |
| _(table \| nil)_ Table containing the matches on success, nil otherwise. |

---

#### `search`

Returns any matches to the given pattern on the given string. _(Uses std::regex\_search)_

```lua
table|nil hook.regex.search(message, pattern, flags);
```

| Parameter Name | Type | Description |
| --- | --- | --- |
| `message` | _string_ | The message to match the pattern within. |
| `pattern` | _string_ | The pattern to match. |
| `flags`   | _number_ | `[Optional]` The regex flags to use while matching. |

| Returns |
| --- |
| _(table \| nil)_ Table containing the matches on success, nil otherwise. |

---

#### `replace`

Returns a replaced string using the given pattern to make replacements. _(Uses std::regex\_replace)_

```lua
string|nil hook.regex.replace(message, pattern, replace, flags);
```

| Parameter Name | Type | Description |
| --- | --- | --- |
| `message` | _string_ | The message to replace the pattern within. |
| `pattern` | _string_ | The pattern to match. |
| `replace` | _string_ | The replacement string. |
| `flags`   | _number_ | `[Optional]` The regex flags to use while matching. |

| Returns |
| --- |
| _(string \| nil)_ The replaced string on success, nil otherwise. |

```lua
string|nil hook.regex.replace(message, pattern, replace, flags);
```

| Parameter Name | Type | Description |
| --- | --- | --- |
| `message` | _string_      | The message to replace the pattern within. |
| `pattern` | _string_      | The pattern to match. |
| `replace` | _function_    | The replacement function to invoke when a match is found to be replaced. |
| `flags`   | _number_      | `[Optional]` The regex flags to use while matching. |

| Returns |
| --- |
| _(string \| nil)_ The replaced string on success, nil otherwise. |

---

#### `split`

Returns a table containing the parts of a split string. _(Uses std::sregex\_token\_iterator)_

```lua
table|nil hook.regex.split(message, pattern, flags);
```

| Parameter Name | Type | Description |
| --- | --- | --- |
| `message` | _string_ | The message to split. |
| `pattern` | _string_ | The pattern to match. |
| `flags`   | _number_ | `[Optional]` The regex flags to use while matching. |

| Returns |
| --- |
| _(table \| nil)_ Table containing the split parts on success, nil otherwise. |

---
