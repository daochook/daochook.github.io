---
title: "Libraries"
pre: "5. "
---

Libraries _(or libs)_ are scripts _(or C DLLs)_ that contain additional functionality that all addons can make use of. Libraries are generally pre-packaged and found within the `/addons/libs/` folder.

Addon developers are free to make their own libraries. Libraries do not need to be placed in the libs folder in order to operate. If you have a library that you have made and feel would useful to all developers, feel free to contact **daochook** staff to see about having your library added to the main release package.

Libraries are easy to use by any addon. Simply `require` them into your addon script(s). For example, most addons will want to make use of the `common` library. This lib will include a handful of common libraries for you. This can be included like:

```lua
require 'common';
```

Libraries that are contained within subfolders can be included by passing the full path to the lib file, replacing any slash character in the path with a period instead. For example:

```lua
require 'sugar.nil';
```

### Compiled Libraries

Compiled libraries, or clibs, are DLLs that expose functionality through a compiled C/C++ DLL file. Lua has a special setup to allow DLLs to be used as libraries when calling `require`. A compiled library must export a `luaopen_` function that contains the name of the file as the require name that will be used. For example, if you have a clib named `hello.dll` then you would require it as:

```lua
require 'hello';
```

Using this setup, `hello.dll` must export a function named `luaopen_hello`.

The library can also expose multiple `luaopen_` functions that are used for specific namespace tables of functions. For example, the library may export multiple functions like this:

```
luaopen_hello_earth
luaopen_hello_world
```

Then a script would require them as:

```lua
require 'hello.earth';
require 'hello.world';
```

For more information on compiled libraries, please check Lua's documentation here: https://www.lua.org/pil/26.2.html

### Included Libraries

**daochook** comes with the following included libraries:

| Library File Name | Usage | Description |
| --- | --- | --- |
| `common.lua`      | `require 'common';`       | Library that includes the various other commonly used lib files. _(It is recommended that your addon includes this!)_ |
| `daoc.lua`        | `local daoc = require 'daoc';` | Library that adds game specific functions and information. _(This library automatically detects your client version and includes the additional libs found within the `/addons/libs/daoc/` folder.)_ |
| `imgui.lua`       | `require 'imgui';`        | Library that adds ImGui related functions and information. |
| `json.lua`        | `require 'json';`         | Library that adds JSON file reading/writing function support. |
| `mimie.lua`       | `require 'mimie';`        | Library used with LuaSocket; defines common web mime types and functionality. |
| `socket.lua`      | `require 'socket';`       | Library used to work with sockets and web requests. |
| `sugar.lua`       | `require 'sugar';`        | Library that _greatly_ expands Lua's base types to add a lot of functional programming features to Lua. |
| `switch.lua`      | `require 'switch';`       | Library that adds a switch-case helper function to Lua. |
| `win32types.lua`  | `require 'win32types';`   | Library that defines common Win32 types with FFI. |

### `daoc` Library

The `daoc` (Dark Age of Camelot) library is used to add game related functionality and information. The main library file will automatically determine your client version, then include the additional version-specific sub-library files found within the `/addons/libs/daoc/` folder. These sub folders are separate into client versions to ensure that the functionality will work on as many clients as possible. It's also easy to add support for other client versions by simply making a copy of an existing folder and updating the function information and pointers appropriately.

This library contains helper functions for interacting with various parts of the game client and its memory/information as well as wrappers to directly call game functions via LuaJIT's FFI library.

### `sugar` Library

The `sugar` library is a lib made by `atom0s` that adds a ton of functional programming helper extensions to the various core objects of Lua.

Sugar includes new functions for the following types and tables:

  - `boolean`
  - `function`
  - `math`
  - `number`
  - `nil`
  - `string`
  - `table`

**Note:** While `sugar` does offer a lot of functionality for Lua tables, it is not enabled by default for all table objects. Instead, you will either need to convert your table to a metatable-enabled one, or create it as one. You can do that easily by using the following syntax instead when creating tables:

```lua
-- Normal table..
local t = { };

-- Sugar enhanced table..
local t = T{ };
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