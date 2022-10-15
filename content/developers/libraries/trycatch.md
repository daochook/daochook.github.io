---
title: "trycatch"
---

The `trycatch` library is a simple library used to create an error handling approach similar to C/C++/C#/etc. try, catch and finally calls.

_The `trycatch` library is based on code by `djfdyuruiry`. https://github.com/djfdyuruiry/lua-try-catch-finally_

### Using The Library

Addons should require the `common` library if they wish to use the `trycatch` library. It is included automatically with it.

```lua
require 'common';
```

### Functions

#### `try`

Implements a try, catch, finally style statement.

```lua
try(func);
```

| Parameter Name | Type | Description |
| --- | --- | --- |
| `func` | _function_ | The function to attempt to run protected from errors. |

| Returns |
| --- |
| _None._ |

---

### Examples

Below are a few examples of using `try`.

You can use `try` without any catch or finally callback, however this is not ideal as it will just hide errors that should otherwise be fixed instead of just ignored.

```lua
try(function ()
    error('Attempt to raise an error..');
end)
```

You can use `try` with a catch callback which will be passed the full error information from when the initial call failed.

```lua
try(function ()
    error('Attempt to raise an error..');
end).catch(function (e)
    -- Print the error information..
    print(e);
end)
```

In some cases, you may want to cleanup objects that were potentially initialized/used with the function being caught for errors. This is generally done in a 'finally' block which runs after the try and catch handlers are invoked, giving a place to ensure cleanup can take place.

```lua
try(function ()
    error('Attempt to raise an error..');
end).catch(function (e)
    -- Print the error information..
    print(e);
end).finally(function ()
    -- Perform any needed cleanup here..
    print('Cleanup can happen here..')
end);
```
