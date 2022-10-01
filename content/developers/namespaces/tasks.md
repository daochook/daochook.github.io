---
title: "tasks"
---

The `tasks` namespace contains functions used to run concurrent functions (coroutines). These functions operate similar to Lua's built in coroutines but offer a bit more flexibility on how they work. **daochook** also extends the built-in coroutine table to include additional functions.

Functions exposed by this namespace are accessed via the prefix: `hook.tasks.`

### Functions

#### `once`

Executes a task once.

```lua
hook.tasks.once(func);
```

| Parameter Name | Type | Description |
| --- | --- | --- |
| `func` | _function_ | The function to execute. |

| Returns |
| --- |
| _None._ |

Executes a task once, after the given delay.

```lua
hook.tasks.once(delay, func);
```

| Parameter Name | Type | Description |
| --- | --- | --- |
| `delay`   | _number_      | The delay to wait before executing the task. |
| `func`    | _function_    | The function to execute. |

| Returns |
| --- |
| _None._ |

---

#### `oncef`

Executes a task once, after the given delay _(in frames)_.

```lua
hook.tasks.once(delay, func);
```

| Parameter Name | Type | Description |
| --- | --- | --- |
| `delay`   | _number_      | The delay to wait before executing the task. _(in frames)_ |
| `func`    | _function_    | The function to execute. |

| Returns |
| --- |
| _None._ |

---

#### `loop`

Loops a task.

```lua
hook.tasks.loop(delay, repeats, repeat_delay, func);
```

| Parameter Name | Type | Description |
| --- | --- | --- |
| `delay`           | _number_      | The delay to wait before executing the task. |
| `repeats`         | _number_      | The number of times to execute the task. |
| `repeat_delay`    | _number_      | The delay to wait between task executions. |
| `func`            | _function_    | The function to execute. |

| Returns |
| --- |
| _None._ |

---

#### `loopf`

Loops a task.

```lua
hook.tasks.loopf(delay, repeats, repeat_delay, func);
```

| Parameter Name | Type | Description |
| --- | --- | --- |
| `delay`           | _number_      | The frame delay to wait before executing the task. |
| `repeats`         | _number_      | The number of times to execute the task. |
| `repeat_delay`    | _number_      | The frame delay to wait between task executions. |
| `func`            | _function_    | The function to execute. |

| Returns |
| --- |
| _None._ |

---

### `coroutine` Extensions

You can see the extensions to the `coroutine` object on the [extensions](/developers/namespaces/extensions/) documentation page.
