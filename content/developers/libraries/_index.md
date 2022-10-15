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

_Click the library file name to open more information specific to that library._

| Library File Name | Usage | Description |
| --- | --- | --- |
| [`common.lua`](common)          | `require 'common';`                     | Library that includes the various other commonly used lib files. _(It is recommended that your addon includes this!)_ |
| [`daoc.lua`](daoc)              | `require 'daoc';`                       | Library that adds game specific functions and information. _(This library automatically detects your client version and includes the additional libs found within the `/addons/libs/daoc/` folder.)_ |
| [`imgui.lua`](imgui)            | `local imgui = require 'imgui';`        | Library that adds ImGui related functions and information. |
| [`json.lua`](json)              | `require 'json';`                       | Library that adds JSON file reading/writing function support. |
| [`mime.lua`](mime)              | `require 'mimie';`                      | Library used with LuaSocket; defines common web mime types and functionality. |
| [`settings.lua`](settings)      | `local settings = require 'settings';`  | Library that can be used for per-character configuration settings in your addon. |
| [`socket.lua`](socket)          | `require 'socket';`                     | Library used to work with sockets and web requests. |
| [`sugar.lua`](sugar)            | `require 'sugar';`                      | Library that _greatly_ expands Lua's base types to add a lot of functional programming features to Lua. |
| [`switch.lua`](switch)          | `require 'switch';`                     | Library that adds a switch-case helper function to Lua. |
| [`trycatch.lua`](trycatch)      | `require 'trycatch';`                   | Library that adds try/catch/finally style support in Lua via `xpcall`. |
| [`win32types.lua`](win32types)  | `require 'win32types';`                 | Library that defines common Win32 types with FFI. |
