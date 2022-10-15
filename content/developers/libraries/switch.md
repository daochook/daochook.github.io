---
title: "switch"
---

The `switch` library is a simple library used to create a C/C++ like switch case statement in Lua.

Lua does not have a stock method of implementing switch statements, thus this library can make that a possibility.

_The `switch` library is based on code by `Ryan Hartlage`. https://github.com/ryanplusplus/switch.lua_

### Using The Library

Addons should require the `common` library if they wish to use the `switch` library. It is included automatically with it.

```lua
require 'common';
```

### Functions

#### `switch`

Implements a switch case style statement.

```lua
any switch(value, cases);
```

| Parameter Name | Type | Description |
| --- | --- | --- |
| `value` | _any_   | The conditional value to switch against. |
| `cases` | _table_ | The table of condition callback functions. |

| Returns |
| --- |
| _(any \| none)_ Any return as desired, or none. |

---

### Examples

Below are a few examples of using `switch`:

```lua
-- Using a switch with a return value..
function get_some_value(arg)
    return switch(arg, T{
        [0]                 = function () return 'Arg Was 0'; end,
        [1]                 = function () return 'Arg Was 1'; end,
        [switch.default]    = function () return 'Arg Was Unknown'; end,
    });
end

-- Using a switch with ranged cases..
function get_some_value(arg)
    return switch(arg, T{
        [table.range(0, 5)] = function () return 'Arg Was 0, 1, 2, 3, 4 or 5'; end,
        [6]                 = function () return 'Arg Was 6'; end,
        [switch.default]    = function () return 'Arg Was Unknown'; end,
    });
end

-- Using a switch with string cases, no return value..
function do_something(arg)
    switch(arg, T{
        ['one']             = function () call_one(); end,
        ['two']             = function () call_two(); end,
        ['three']           = function () call_three(); end,
        [switch.default]    = function () error('invalid case'); end,
    });
end
```
