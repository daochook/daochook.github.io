---
title: "memory"
---

The `memory` namespace contains functions that allow addons to access the game client memory in multiple ways.

{{% notice tip %}}
You can also make use of the `ffi` library to access memory with more features such as casting to actual C style structures.
{{% /notice %}}

Functions exposed by this namespace are accessed via the prefix: `hook.memory.`

### Functions

### `get_base`

Returns the base address of a loaded module.

```lua
number hook.memory.get_base(name);
```

| Parameter Name | Type | Description |
| --- | --- | --- |
| `name` | _string_ | `[Optional]` The name of the module. |

| Returns |
| --- |
| _(number)_ The base address of of the module on success, 0 otherwise. |

_If `name` is nil or an empty string, then the `game.dll` module is used by default._

---

### `get_size`

Returns the size of a loaded module.

```lua
number hook.memory.get_size(name);
```

| Parameter Name | Type | Description |
| --- | --- | --- |
| `name` | _string_ | `[Optional]` The name of the module. |

| Returns |
| --- |
| _(number)_ The size of of the module on success, 0 otherwise. |

_If `name` is nil or an empty string, then the `game.dll` module is used by default._

---

### `protect`

```lua
boolean, number hook.memory.protect(addr, size, protection);
```

Sets the memory protection of the given address.

| Parameter Name | Type | Description |
| --- | --- | --- |
| `addr`        | _number_ | The address to change the protection of. |
| `size`        | _number_ | The size of the region to change. |
| `protection`  | _number_ | The new protection value to change to. |

| Returns |
| --- |
| _(boolean, number)_ The return value from `VirtualProtect` and the previous protection value. |

---

### `unprotect`

```lua
boolean, number hook.memory.unprotect(addr, size);
```

Sets the memory protection of the given address to `PAGE_EXECUTE_READWRITE`.

| Parameter Name | Type | Description |
| --- | --- | --- |
| `addr` | _number_ | The address to change the protection of. |
| `size` | _number_ | The size of the region to change. |

| Returns |
| --- |
| _(boolean, number)_ The return value from `VirtualProtect` and the previous protection value. |

---

### `alloc`

Allocates memory within the process and returns the address to where it was allocated at. _(Uses `VirtualAlloc` to allocate memory.)_

```lua
number|nil hook.memory.alloc(size);
```

| Parameter Name | Type | Description |
| --- | --- | --- |
| `size` | _number_ | The size of the region to allocate. |

| Returns |
| --- |
| _(number \| nil)_ The address of the allocated memory on success, nil otherwise. |

---

### `dealloc`

Deallocates memory that was previously allocated via `alloc`.

```lua
boolean hook.memory.dealloc(addr);
```

| Parameter Name | Type | Description |
| --- | --- | --- |
| `addr` | _number_ | The address of the memory to deallocate. |

| Returns |
| --- |
| _(boolean)_ The return value from `VirtualFree`. |

---

### `find`

Scans for a pattern of bytes within the given module.

```lua
number hook.memory.find(name, pattern, offset, count);
```

| Parameter Name | Type | Description |
| --- | --- | --- |
| `name`    | _string_ | `[Optional]` The name of the module to scan within. |
| `pattern` | _string_ | The pattern to scan for. |
| `offset`  | _number_ | The offset from the found address to be added to the return. |
| `count`   | _number_ | The count of the result to use if the pattern is found more than once. |

| Returns |
| --- |
| _(number)_ The address where the pattern was found on success, 0 otherwise. |

_If `name` is nil or an empty string, then the `game.dll` module is used by default._

```lua
number hook.memory.find(base, size, pattern, offset, count);
```

| Parameter Name | Type | Description |
| --- | --- | --- |
| `base`    | _number_ | The address to start scanning at. |
| `size`    | _number_ | The size to scan within. |
| `pattern` | _string_ | The pattern to scan for. |
| `offset`  | _number_ | The offset from the found address to be added to the return. |
| `count`   | _number_ | The count of the result to use if the pattern is found more than once. |

| Returns |
| --- |
| _(number)_ The address where the pattern was found on success, 0 otherwise. |

_If `base` and `size` are both 0, then the `game.dll` module is used by default._

---

### `read_int8`

Reads a value from memory. _(int8)_

```lua
number hook.memory.read_int8(addr);
```

| Parameter Name | Type | Description |
| --- | --- | --- |
| `addr` | _number_ | The address to read the value from. |

| Returns |
| --- |
| _(number)_ The read value on success, 0 otherwise. |

---

### `read_int16`

Reads a value from memory. _(int16)_

```lua
number hook.memory.read_int16(addr);
```

| Parameter Name | Type | Description |
| --- | --- | --- |
| `addr` | _number_ | The address to read the value from. |

| Returns |
| --- |
| _(number)_ The read value on success, 0 otherwise. |

---

### `read_int32`

Reads a value from memory. _(int32)_

```lua
number hook.memory.read_int32(addr);
```

| Parameter Name | Type | Description |
| --- | --- | --- |
| `addr` | _number_ | The address to read the value from. |

| Returns |
| --- |
| _(number)_ The read value on success, 0 otherwise. |

---

### `read_int64`

Reads a value from memory. _(int64)_

```lua
number hook.memory.read_int64(addr);
```

| Parameter Name | Type | Description |
| --- | --- | --- |
| `addr` | _number_ | The address to read the value from. |

| Returns |
| --- |
| _(number)_ The read value on success, 0 otherwise. |

---

### `read_uint8`

Reads a value from memory. _(uint8)_

```lua
number hook.memory.read_uint8(addr);
```

| Parameter Name | Type | Description |
| --- | --- | --- |
| `addr` | _number_ | The address to read the value from. |

| Returns |
| --- |
| _(number)_ The read value on success, 0 otherwise. |

---

### `read_uint16`

Reads a value from memory. _(uint16)_

```lua
number hook.memory.read_uint16(addr);
```

| Parameter Name | Type | Description |
| --- | --- | --- |
| `addr` | _number_ | The address to read the value from. |

| Returns |
| --- |
| _(number)_ The read value on success, 0 otherwise. |

---

### `read_uint32`

Reads a value from memory. _(uint32)_

```lua
number hook.memory.read_uint32(addr);
```

| Parameter Name | Type | Description |
| --- | --- | --- |
| `addr` | _number_ | The address to read the value from. |

| Returns |
| --- |
| _(number)_ The read value on success, 0 otherwise. |

---

### `read_uint64`

Reads a value from memory. _(uint64)_

```lua
number hook.memory.read_uint64(addr);
```

| Parameter Name | Type | Description |
| --- | --- | --- |
| `addr` | _number_ | The address to read the value from. |

| Returns |
| --- |
| _(number)_ The read value on success, 0 otherwise. |

---

### `read_float`

Reads a value from memory. _(float)_

```lua
number hook.memory.read_float(addr);
```

| Parameter Name | Type | Description |
| --- | --- | --- |
| `addr` | _number_ | The address to read the value from. |

| Returns |
| --- |
| _(number)_ The read value on success, 0 otherwise. |

---

### `read_double`

Reads a value from memory. _(double)_

```lua
number hook.memory.read_double(addr);
```

| Parameter Name | Type | Description |
| --- | --- | --- |
| `addr` | _number_ | The address to read the value from. |

| Returns |
| --- |
| _(number)_ The read value on success, 0 otherwise. |

---

### `read_array`

Reads an array of bytes from memory.

```lua
table|nil hook.memory.read_array(addr, size);
```

| Parameter Name | Type | Description |
| --- | --- | --- |
| `addr` | _number_ | The address to read the value from. |
| `size` | _number_ | The size of data to read. |

| Returns |
| --- |
| _(table \| nil)_ The read array on success, nil otherwise. |

---

### `read_string`

Reads a string from memory.

```lua
string|nil hook.memory.read_string(addr, size);
```

| Parameter Name | Type | Description |
| --- | --- | --- |
| `addr` | _number_ | The address to read the value from. |
| `size` | _number_ | The size of data to read. |

| Returns |
| --- |
| _(string \| nil)_ The read string on success, nil otherwise. |

---

### `read_literal`

Reads a string literal from memory.

```lua
string|nil hook.memory.read_literal(addr, size);
```

| Parameter Name | Type | Description |
| --- | --- | --- |
| `addr` | _number_ | The address to read the value from. |
| `size` | _number_ | The size of data to read. |

| Returns |
| --- |
| _(string \| nil)_ The read string literal on success, nil otherwise. |

---

### `write_int8`

Writes a value to memory. _(int8)_

```lua
hook.memory.write_int8(addr, value);
```

| Parameter Name | Type | Description |
| --- | --- | --- |
| `addr`    | _number_ | The address to write the value to. |
| `value`   | _number_ | The value to write. |

| Returns |
| --- |
| _None._ |

---

### `write_int16`

Writes a value to memory. _(int16)_

```lua
hook.memory.write_int16(addr, value);
```

| Parameter Name | Type | Description |
| --- | --- | --- |
| `addr`    | _number_ | The address to write the value to. |
| `value`   | _number_ | The value to write. |

| Returns |
| --- |
| _None._ |

---

### `write_int32`

Writes a value to memory. _(int32)_

```lua
hook.memory.write_int32(addr, value);
```

| Parameter Name | Type | Description |
| --- | --- | --- |
| `addr`    | _number_ | The address to write the value to. |
| `value`   | _number_ | The value to write. |

| Returns |
| --- |
| _None._ |

---

### `write_int64`

Writes a value to memory. _(int64)_

```lua
hook.memory.write_int64(addr, value);
```

| Parameter Name | Type | Description |
| --- | --- | --- |
| `addr`    | _number_ | The address to write the value to. |
| `value`   | _number_ | The value to write. |

| Returns |
| --- |
| _None._ |

---

### `write_uint8`

Writes a value to memory. _(uint8)_

```lua
hook.memory.write_uint8(addr, value);
```

| Parameter Name | Type | Description |
| --- | --- | --- |
| `addr`    | _number_ | The address to write the value to. |
| `value`   | _number_ | The value to write. |

| Returns |
| --- |
| _None._ |

---

### `write_uint16`

Writes a value to memory. _(uint16)_

```lua
hook.memory.write_uint16(addr, value);
```

| Parameter Name | Type | Description |
| --- | --- | --- |
| `addr`    | _number_ | The address to write the value to. |
| `value`   | _number_ | The value to write. |

| Returns |
| --- |
| _None._ |

---

### `write_uint32`

Writes a value to memory. _(uint32)_

```lua
hook.memory.write_uint32(addr, value);
```

| Parameter Name | Type | Description |
| --- | --- | --- |
| `addr`    | _number_ | The address to write the value to. |
| `value`   | _number_ | The value to write. |

| Returns |
| --- |
| _None._ |

---

### `write_uint64`

Writes a value to memory. _(uint64)_

```lua
hook.memory.write_uint64(addr, value);
```

| Parameter Name | Type | Description |
| --- | --- | --- |
| `addr`    | _number_ | The address to write the value to. |
| `value`   | _number_ | The value to write. |

| Returns |
| --- |
| _None._ |

---

### `write_float`

Writes a value to memory. _(float)_

```lua
hook.memory.write_float(addr, value);
```

| Parameter Name | Type | Description |
| --- | --- | --- |
| `addr`    | _number_ | The address to write the value to. |
| `value`   | _number_ | The value to write. |

| Returns |
| --- |
| _None._ |

---

### `write_double`

Writes a value to memory. _(double)_

```lua
hook.memory.write_double(addr, value);
```

| Parameter Name | Type | Description |
| --- | --- | --- |
| `addr`    | _number_ | The address to write the value to. |
| `value`   | _number_ | The value to write. |

| Returns |
| --- |
| _None._ |

---

### `write_array`

Writes an array of values to memory.

```lua
hook.memory.write_array(addr, value);
```

| Parameter Name | Type | Description |
| --- | --- | --- |
| `addr`    | _number_  | The address to write the value to. |
| `value`   | _table_   | The array of values to write. |

| Returns |
| --- |
| _None._ |

---

### `write_string`

Writes a string to memory.

```lua
hook.memory.write_string(addr, str, size);
```

| Parameter Name | Type | Description |
| --- | --- | --- |
| `addr`    | _number_  | The address to write the value to. |
| `str`     | _string_  | The string value to write. |
| `size`    | _number_  | `[Optional]` The length of the string to write. |

| Returns |
| --- |
| _None._ |

_If `size` is not given, then the length of the string is automatically determined._

---
