---
title: "sugar"
---

The `sugar` library is a set of sub-libraries that adds a ton of functional programming helper extensions to the various core objects of Lua.

### Using The Library

Addons should require the `common` library if they wish to use the `sugar` library. It is included automatically with it.

```lua
require 'common';
```

Below you can find some information regarding each sub-library of `sugar`.

_Because of how many functions this collection of sub-libraries implements, full documentation will not be made for every function. Please refer to the actual source files for more information on all of the functions available._

### `boolean`

Implements various helper functions used with `boolean` type values.

_This sub-library also overrides the default `boolean` type metatable to expose these new functions directly onto `boolean` type values._

### `function`

Implements various helper functions used with `function` type values.

_This sub-library also overrides the default `function` type metatable to expose these new functions directly onto `function` type values._

### `math`

Implements various helper functions that extend the default `math.` global table.

_This sub-library also overrides the default `number` type metatable to expose these new functions directly onto `number` type values._

### `nil`

{{% notice warning %}}
The use of this sub-library is considered dangerous!\
Please read the below information before including this sub-library in your addon!
{{% /notice %}}

This sub-library will override the default metatable for the `nil` type. This is considered dangerous because of what this will do to the default functionality of Lua.

Lua, by default, will raise an error if you attempt to call or index a nil value. This is good practice to avoid unintended situations in code and should generally **ALWAYS** be followed. This sub-library will remove those restrictions of Lua and allow you to attempt to call a nil function, inde a nil object/value, etc.

  - This **SHOULD NOT** be used to avoid proper error handling.
  - This **SHOULD NOT** be used to avoid fixing problems with code.

_Please **DO NOT** use this sub-library unless you know what you're doing!_

If you do wish to use this feature, then you will need to adjust how you include the `common` library to call the enabler function for it:

```lua
local common = require 'common';

common.sugar.enable_nil_sugar();    -- Enables the nil metatable override..
common.sugar.disable_nil_sugar();   -- Disables the nil metatable override..
```

### `string`

Implements various helper functions that extend the default `string.` global table.

_This sub-library also overrides the default `string` type metatable to expose these new functions directly onto `string` type values._

### `table`

Implements various helper functions that extend the default `table.` global table.

Because of how Lua functions, it is not possible to fully override the `table` type metatable and have additional functionality applied to any `table` type. To get around this, `sugar` implements its own `table` initialization call. This wraps the given table with an enhanced metatable giving access to call all `table` functions directly on the type. You can use this function to either create a new or 'upgrade' an existing table.

```lua
-- Normal Lua Table..
local t1 = { };

-- Sugar Enhanced Table..
local t2 = T{ };

-- Sugar Enhanced Table Upgrade..
local t3 = T(t1);
```

When you create a `sugar` enhanced table, this enables all of `sugar`'s features that are extending the metatable of the table object.

Here is an example:

```lua
-- Normal Lua table usage example..
local t = { };
table.insert(t, 2);
table.insert(t, 3);
table.insert(t, 1);
table.sort(t);

for k, v in pairs (t) do print(v); end

-- Sugar enhanced table usage example..
local t = T{ };
t:insert(2);
t:insert(3);
t:insert(1);
t:sort();
t:each(function (v) print(v); end);
```

_Sugar is very powerful in how much it can allow you to transform normal Lua code into a functional programming syntax._
