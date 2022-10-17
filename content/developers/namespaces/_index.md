---
title: "Functions & Namespaces"
pre: "4. "
weight: 4
---

**daochook** includes a handful of various helper functions that are exposed to each addons Lua state. These functions are separated into namespaces that make it cleaner and easier to read when being accessed. Below is a table of each of the namespaces that are exposed from **daochook**.

### Functions (Globals)

#### `print`

Overridden from the stock Lua print functionality. Instead, calling print will print the given message to the games chat window using the default message mode. `(1)`

```lua
print(...);
```

| Parameter Name | Type | Description |
| --- | --- | --- |
| `...` | `string` | The message(s) to print. |

| Returns |
| --- |
| _None._ |

---

#### `dbgprint`

Debug print helper. Prints the given message to the system debug stream.

```lua
dbgprint(...);
```

| Parameter Name | Type | Description |
| --- | --- | --- |
| `...` | `string` | The message(s) to print. |

| Returns |
| --- |
| _None._ |

_To view these messages, use a tool such as DbgView, DbgView++ or similar._

---

### Namespaces

_Click the namespace name to go to that namespaces individual documentation page._

| Namespace Name | Description |
| --- | --- |
| [`bits`](/developers/namespaces/bits/)            | Contains functions related to bit and byte packing/unpacking. |
| [`events`](/developers/namespaces/events/)        | Contains functions related to **daochook** events. |
| [`extensions`](/developers/namespaces/extensions/)| Contains functions that extend default Lua types. |
| [`fs`](/developers/namespaces/fs/)                | Contains functions related to file I/O. |
| [`game`](/developers/namespaces/game/)            | Contains functions related to game client functions and information. |
| [`hook`](/developers/namespaces/hook/)            | Contains functions related to **daochook** functions and information. |
| [`imgui`](/developers/namespaces/imgui/)          | Contains functions related to ImGui. |
| [`memory`](/developers/namespaces/memory/)        | Contains functions related to memory read/write operations. |
| [`misc`](/developers/namespaces/misc/)            | Contains miscellaneous functions that don't fit into another namespace. |
| [`regex`](/developers/namespaces/regex/)          | Contains functions related to regular expression operations. |
| [`tasks`](/developers/namespaces/tasks/)          | Contains functions related to tasks. |
| [`time`](/developers/namespaces/time/)            | Contains functions related to time. |
