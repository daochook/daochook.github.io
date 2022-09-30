---
title: "events"
---

The `events` namespace contains functions that are used for working with **daochook** events.

### Functions

#### `register`

Registers a new callback function to the given event.

```lua
boolean hook.events.register(event_name, event_alias, callback_func);
```

| Parameter Name | Type | Description |
| --- | --- | --- |
| `event_name`      | _string_      | The name of the event to register this callback to. |
| `event_alias`     | _string_      | The alias for this callback. |
| `callback_func`   | _function_    | The function to invoke when the event is raised. |

| Returns |
| --- |
| _(boolean)_ True on success, false otherwise. |

---

#### `unregister`

Unregisters an existing callback from the given event.

```lua
boolean hook.events.unregister(event_name, event_alias);
```

| Parameter Name | Type | Description |
| --- | --- | --- |
| `event_name`      | _string_      | The name of the event to unregister the existing callback for. |
| `event_alias`     | _string_      | The alias for the existing callback to unregister. |

| Returns |
| --- |
| _(boolean)_ True on success, false otherwise. |
