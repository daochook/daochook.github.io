---
title: "fs (File System)"
---

The `fs` namespace contains functions that are used for working with file system operations. Lua does contain some basic file I/O functionality, but this namespace includes a handful of additional functions that make up for where Lua is lacking.

{{% notice tip %}}
These file system functions make use of the C++ `std::filesystem` header. The functions are named the same/similar.\
For more information on those functions, please visit: https://en.cppreference.com/w/cpp/filesystem
{{% /notice %}}

Functions exposed by this namespace are accessed via the prefix: `hook.fs.`

### Functions

#### `create_directory`, `create_dir`

Creates the given directory. _Any folder within the given path that do not exist will also be created._

```lua
boolean hook.fs.create_directory(path);
boolean hook.fs.create_dir(path);
```

| Parameter Name | Type | Description |
| --- | --- | --- |
| `path` | _string_ | The name, or path, of the folder to create. |

| Returns |
| --- |
| _(boolean)_ True on success, false otherwise. |

---

#### `current_directory`, `current_dir`

Returns, or sets, the current directory.

```lua
string hook.fs.current_directory();
string hook.fs.current_dir();

boolean hook.fs.current_directory(path);
boolean hook.fs.current_dir(path);
```

| Parameter Name | Type | Description |
| --- | --- | --- |
| `path` | _string_ | `[Optional]` The path to set the current directory to, if setting. |

| Returns |
| --- |
| **get**: _(string)_ The current directory path. |
| **set**: _(boolean)_ True on success, false otherwise. |

---

#### `equivalent`, `equals`

Returns if two paths are the equal.

```lua
boolean hook.fs.equivalent(path1, path2);
boolean hook.fs.equals(path1, path2);
```

| Parameter Name | Type | Description |
| --- | --- | --- |
| `path1` | _string_ | The first path to compare. |
| `path2` | _string_ | The second path to compare. |

| Returns |
| --- |
| _(boolean)_ True if the paths are equal, false otherwise. |

---

#### `exists`

Returns if the given path exists. _Can be a file or folder path._

```lua
boolean hook.fs.exists(path);
```

| Parameter Name | Type | Description |
| --- | --- | --- |
| `path` | _string_ | The path to check. |

| Returns |
| --- |
| _(boolean)_ True if the path exists, false otherwise. |

---

#### `get_directory`, `get_dir`

Returns the contents of the given directory.

```lua
table|nil hook.fs.get_directory(path);
table|nil hook.fs.get_dir(path);
```

| Parameter Name | Type | Description |
| --- | --- | --- |
| `path` | _string_     | The path to obtain the contents of. |
| `mask` | _string_     | `[Optional]` The filter mask to apply when returning files. |
| `subs` | _boolean_    | `[Optional]` Flag that states if sub folders should be included. |

| Returns |
| --- |
| _(table \| nil)_ Table of the directory contents on success, nil otherwise. |

---

#### `normalize`

Returns the normalized path.

```lua
string|nil hook.fs.normalize(path);
```

| Parameter Name | Type | Description |
| --- | --- | --- |
| `path` | _string_ | The path to normalize. |

| Returns |
| --- |
| _(string \| nil)_ The normalized path on success, nil otherwise. |

---

#### `remove`

Removes, or deletes, the given path. _Can be a file or folder path._

```lua
boolean hook.fs.remove(path);
```

| Parameter Name | Type | Description |
| --- | --- | --- |
| `path` | _string_ | The path to remove. |

| Returns |
| --- |
| _(boolean)_ True on success, false otherwise. |

---

#### `rename`

Renames the file or folder.

```lua
boolean hook.fs.rename(path);
```

| Parameter Name | Type | Description |
| --- | --- | --- |
| `path` | _string_ | The path to rename. |

| Returns |
| --- |
| _(boolean)_ True on success, false otherwise. |

---

#### `size`

Returns the size of the given path. _Can be a file or folder._

```lua
number hook.fs.size(path);
```

| Parameter Name | Type | Description |
| --- | --- | --- |
| `path` | _string_ | The path to obtain the size of. |

| Returns |
| --- |
| _(number)_ The size on success, 0 otherwise. |

---

#### `space`

Returns the space of the given path. _Can be a file or folder._

```lua
table|nil hook.fs.space(path);
```

| Parameter Name | Type | Description |
| --- | --- | --- |
| `path` | _string_ | The path to obtain the space of. |

| Returns |
| --- |
| _(table \| nil)_ Table containing the space information on success, nil otherwise. |

The returned table contains the following properties:

  - `available` _(number)_ - The total size of the file system. _(in bytes)_
  - `capacity` _(number)_ - The free space of the file system. _(in bytes)_
  - `free` _(number)_ - The free space of the file system, to a non-privileged process. _(in bytes)_

---

#### `status`

Returns the status of the given path. _Can be a file or folder._

```lua
table|nil hook.fs.status(path);
```

| Parameter Name | Type | Description |
| --- | --- | --- |
| `path` | _string_ | The path to obtain the status of. |

| Returns |
| --- |
| _(table \| nil)_ Table containing the status information on success, nil otherwise. |

The returned table contains the following properties:

  - `permissions` _(number)_ - The file or folder permissions.
  - `exists` _(boolean)_ - Flag that states if the path exists.
  - `is_regular_file` _(boolean)_ - Flag that states if the path is a regular file.
  - `is_directory` _(boolean)_ - Flag that states if the path is a directory.
  - `is_block_file` _(boolean)_ - Flag that states if the path is a block file.
  - `is_character_file` _(boolean)_ - Flag that states if the path is a character file.
  - `is_fifo` _(boolean)_ - Flag that states if the path is a FIFO file.
  - `is_socket` _(boolean)_ - Flag that states if the path is a socket.
  - `is_symlink` _(boolean)_ - Flag that states if the path is a symbolic link.

---

### Properties

#### `preferred_separator`

Contains the preferred slash character for paths.

```lua
local sep = hook.fs.preferred_separator;
print(sep); -- Prints \
```

---
