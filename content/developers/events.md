---
title: "Events"
pre: "3. "
weight: 3
---

Events are one of the main ways addons can be used to interact with the game client. **daochook** hooks onto multiple game functions and then creates/raises an event internally when one of those functions is invoked. When this happens, the internal addon manager will raise the event in every loaded addon whom has registered one or more callback functions to the event being raised. _Addons can register more than one callback to an event if needed._

Addons are not required to register to any events in order to be considered valid. Events are entirely optional and is best to not register to any event unless you absolutely need information from it. It's a waste of performance to register to events that you are not actually using.

### Event Functions

**daochook** exposes two main functions for registering and unregistering from events.

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

### Event Registration

Addons can register to an event using the `hook.events.register(...)` function. Similarly, an addon can unregister from an event using the `hook.events.unregister(...)` function.

When registering to an event, you can write the callback function in multiple formats. The main two formats are considered `short-hand` and `long-hand`. Generally, `short-hand` is the recommended means of writing code as it saves space.

#### Short-hand Method

```lua
hook.events.register('load', 'load_cb', function ()
    print('Load event was fired.');
end);
```

#### Long-hand Method

```lua
local function load_callback()
    print('Load event was fired.');
end
hook.events.register('load', 'load_cb', load_callback);
```

### Registering Multiple Callbacks

If you need to register to an event multiple times, then you must pass a unique alias for each time you register to the event. For example:

```lua

hook.events.register('load', 'load_cb1', function ()
    print('Load event was fired. (1)');
end);
hook.events.register('load', 'load_cb2', function ()
    print('Load event was fired. (2)');
end);
```

If you do not pass a unique alias, then the existing registered callback will be overwritten.

### Available Events

**daochook** currently exposes the following list of events. _Click the name of the event to navigate to its specific information entry._

| Event Name | Event Description |
| --- | --- |
| [`load`](#event-load)                         | Event raised when the addon is being loaded. |
| [`unload`](#event-unload)                     | Event raised when the addon is being unloaded. |
| [`command`](#event-command)                   | Event raised when the game client is handling a command. |
| [`message`](#event-message)                   | Event raised when the game client is about to print a message to the chat/combat windows. |
| [`packet_recv`](#event-packet_recv)           | Event raised when the game client receives a packet. |
| [`packet_send`](#event-packet_send)           | Event raised when the game client sends a packet. |
| [`d3d_prereset`](#event-d3d_prereset)         | Event raised when the game client is about to reset the graphics device. |
| [`d3d_postreset`](#event-d3d_postreset)       | Event raised when the game client has finished resetting the graphics device. |
| [`d3d_beginscene`](#event-d3d_beginscene)     | Event raised when the game client is beginning a new scene. |
| [`d3d_endscene`](#event-d3d_endscene)         | Event raised when the game client is ending a scene. |
| [`d3d_present`](#event-d3d_present)           | Event raised when the game client is presenting the scene. |
| [`d3d_renderstate`](#event-d3d_renderstate)   | Event raised when the game client is setting a render state. |
| [`d3d_dip`](#event-d3d_dip)                   | Event raised when the game client is about to render a primitive. |
| [`d3d_dipup`](#event-d3d_dipup)               | Event raised when the game client is about to render a primitive. |
| [`d3d_dp`](#event-d3d_dp)                     | Event raised when the game client is about to render a primitive. |
| [`d3d_dpup`](#event-d3d_dpup)                 | Event raised when the game client is about to render a primitive. |

### Event Arguments Information

Some of the events that can be raised within an addon have arguments that are passed to their callback functions. These arguments are passed as a single table to help improve performance when calling between the C++ and Lua bounds. _This is similar to how `C#` handles events._

If an event has any arguments, you can find more information for those arguments in the information listed below. The argument information tables explain each of the arguments that the given event has access to. They also mark if the argument is `read-only` or not. When an argument is `read-only`, it cannot be modified or the addon will throw an error. Any argument not marked as `read-only` can be modified.

When an argument is modified, all addons that will receive the event after yours will see the new modified value. They will also be given the ability to further modify the value if they see fit. Once all addons have handled the event, if it was not blocked, the client will process the data using the modified values as if that was the original data to begin with.

#### Injected Events

Events that have an `e.injected` argument can determine if the event came from the actual game client, or if it was injected by **daochook** or another addon.

{{% notice tip %}}
It is best practice to not block or modify injected data as another addon has deemed it important enough to be injected. You can increase performance if you exit an event callback early if the event was injected and you don't need to process it.
{{% /notice %}}

#### Blocked Events

Events that have an `e.blocked` argument can determine if the event has been blocked by **daochook** or another addon. Once an event has been blocked, it cannot be unblocked. Setting `e.blocked` to false will not change any previous true value it was set to. If you wish to block the event from reaching the client in your addon, you can set this to true to cause it to be blocked. ie. `e.blocked = true;`

{{% notice tip %}}
It is best practice to check if an event is blocked and ignore it if you do not need to further act on it. You can increase performance if you exit an event callback early if the event was already blocked and you have no need to process it.
{{% /notice %}}

### Event: `load`

Event raised when the addon is being loaded.

{{% expand "Click for more event information.." %}}
```lua
hook.events.registered('load', 'load_cb', function ()
end);
```

| Argument Name | Type | Description |
| --- | --- | --- |
| _None._ | --- | --- |

---
{{% /expand %}}

### Event: `unload`

Event raised when the addon is being unloaded.

{{% expand "Click for more event information.." %}}
```lua
hook.events.registered('unload', 'unload_cb', function ()
end);
```

| Argument Name | Type | Description |
| --- | --- | --- |
| _None._ | --- | --- |

---
{{% /expand %}}

### Event: `command`

Event raised when the game client is handling a command.

{{% expand "Click for more event information.." %}}
```lua
hook.events.registered('command', 'command_cb', function (e)
end);
```

| Argument Name | Type | Description |
| --- | --- | --- |
| `e.mode`              | _number_  | `[Read Only]` The command mode. |
| `e.imode`             | _number_  | `[Read Only]` The command input mode. |
| `e.command`           | _string_  | `[Read Only]` The command string. |
| `e.modified_mode`     | _number_  | The modified command mode. |
| `e.modified_imode`    | _number_  | The modified command input mode. |
| `e.modified_command`  | _string_  | The modified command string. |
| `e.injected`          | _boolean_ | `[Read Only]` Flag that states if the event was injected by daochook or another addon. |
| `e.blocked`           | _boolean_ | Flag that states if the event has been blocked by daochook or another addon. |

---
{{% /expand %}}

### Event: `message`

Event raised when the game client is about to print a message to the chat/combat windows.

{{% expand "Click for more event information.." %}}
```lua
hook.events.registered('message', 'message_cb', function (e)
end);
```

| Argument Name | Type | Description |
| --- | --- | --- |
| `e.mode`              | _number_  | `[Read Only]` The message mode. |
| `e.message`           | _string_  | `[Read Only]` The message string. |
| `e.modified_mode`     | _number_  | The modified message mode. |
| `e.modified_message`  | _string_  | The modified message string. |
| `e.injected`          | _boolean_ | `[Read Only]` Flag that states if the event was injected by daochook or another addon. |
| `e.blocked`           | _boolean_ | Flag that states if the event has been blocked by daochook or another addon. |

---
{{% /expand %}}

### Event: `packet_recv`

Event raised when the game client receives a packet.

{{% expand "Click for more event information.." %}}
```lua
hook.events.registered('packet_recv', 'packet_recv_cb', function (e)
end);
```

| Argument Name | Type | Description |
| --- | --- | --- |
| `e.opcode`            | _number_  | `[Read Only]` The packet opcode. |
| `e.unknown`           | _number_  | `[Read Only]` Unknown. _(Generally zero.)_ |
| `e.session_id`        | _number_  | `[Read Only]` The client session id. |
| `e.data`              | _string_  | `[Read Only]` The packet data. _(As a string literal.)_ |
| `e.data_raw`          | _void*_   | `[Read Only]` The packet data. _(As a raw pointer, for use with FFI.)_ |
| `e.data_modified`     | _string_  | The modified packet data. _(As a string literal.)_ |
| `e.data_modified_raw` | _void*_   | The modified packet data. _(As a raw pointer, for use with FFI.)_ |
| `e.size`              | _number_  | `[Read Only]` The packet size. |
| `e.state`             | _number_  | `[Read Only]` The game state pointer. |
| `e.injected`          | _boolean_ | `[Read Only]` Flag that states if the event was injected by daochook or another addon. |
| `e.blocked`           | _boolean_ | Flag that states if the event has been blocked by daochook or another addon. |

---
{{% /expand %}}

### Event: `packet_send`

Event raised when the game client sends a packet.

{{% expand "Click for more event information.." %}}
```lua
hook.events.registered('packet_send', 'packet_send_cb', function (e)
end);
```

| Argument Name | Type | Description |
| --- | --- | --- |
| `e.opcode`            | _number_  | `[Read Only]` The packet opcode. |
| `e.data`              | _string_  | `[Read Only]` The packet data. _(As a string literal.)_ |
| `e.data_raw`          | _void*_   | `[Read Only]` The packet data. _(As a raw pointer, for use with FFI.)_ |
| `e.data_modified`     | _string_  | The modified packet data. _(As a string literal.)_ |
| `e.data_modified_raw` | _void*_   | The modified packet data. _(As a raw pointer, for use with FFI.)_ |
| `e.size`              | _number_  | `[Read Only]` The packet size. |
| `e.parameter`         | _number_  | `[Read Only]` The packet parameter. |
| `e.injected`          | _boolean_ | `[Read Only]` Flag that states if the event was injected by daochook or another addon. |
| `e.blocked`           | _boolean_ | Flag that states if the event has been blocked by daochook or another addon. |

---
{{% /expand %}}

### Event: `d3d_prereset`

Event raised when the game client is about to reset the graphics device.

{{% expand "Click for more event information.." %}}
```lua
hook.events.registered('d3d_prereset', 'd3d_prereset_cb', function (e)
end);
```

| Argument Name | Type | Description |
| --- | --- | --- |
| `e.back_buffer_width`             | _number_  | `[Read Only]` The back buffer width. |
| `e.back_buffer_height`            | _number_  | `[Read Only]` The back buffer height. |
| `e.back_buffer_format`            | _number_  | `[Read Only]` The back buffer format. |
| `e.back_buffer_count`             | _number_  | `[Read Only]` The back buffer count. |
| `e.multisample_type`              | _number_  | `[Read Only]` The multisample type. |
| `e.multisample_quality`           | _number_  | `[Read Only]` The multisample quality. |
| `e.swap_effect`                   | _number_  | `[Read Only]` The swap effect. |
| `e.device_window`                 | _number_  | `[Read Only]` The device window handle. |
| `e.windowed`                      | _boolean_ | `[Read Only]` The windowed mode flag. |
| `e.enable_auto_depth_stencil`     | _boolean_ | `[Read Only]` The enable auto depth stencil flag. |
| `e.auto_depth_stencil_format`     | _number_  | `[Read Only]` The auto depth stencil format. |
| `e.flags`                         | _number_  | `[Read Only]` The flags. |
| `e.fullscreen_refresh_rate_in_hz` | _number_  | `[Read Only]` The fullscreen refresh rate in hz. |
| `e.presentation_interval`         | _number_  | `[Read Only]` The presentation interval. |

---
{{% /expand %}}

### Event: `d3d_postreset`

Event raised when the game client has finished resetting the graphics device.

{{% expand "Click for more event information.." %}}
```lua
hook.events.registered('d3d_postreset', 'd3d_postreset_cb', function (e)
end);
```

| Argument Name | Type | Description |
| --- | --- | --- |
| `e.back_buffer_width`             | _number_  | `[Read Only]` The back buffer width. |
| `e.back_buffer_height`            | _number_  | `[Read Only]` The back buffer height. |
| `e.back_buffer_format`            | _number_  | `[Read Only]` The back buffer format. |
| `e.back_buffer_count`             | _number_  | `[Read Only]` The back buffer count. |
| `e.multisample_type`              | _number_  | `[Read Only]` The multisample type. |
| `e.multisample_quality`           | _number_  | `[Read Only]` The multisample quality. |
| `e.swap_effect`                   | _number_  | `[Read Only]` The swap effect. |
| `e.device_window`                 | _number_  | `[Read Only]` The device window handle. |
| `e.windowed`                      | _boolean_ | `[Read Only]` The windowed mode flag. |
| `e.enable_auto_depth_stencil`     | _boolean_ | `[Read Only]` The enable auto depth stencil flag. |
| `e.auto_depth_stencil_format`     | _number_  | `[Read Only]` The auto depth stencil format. |
| `e.flags`                         | _number_  | `[Read Only]` The flags. |
| `e.fullscreen_refresh_rate_in_hz` | _number_  | `[Read Only]` The fullscreen refresh rate in hz. |
| `e.presentation_interval`         | _number_  | `[Read Only]` The presentation interval. |

---
{{% /expand %}}

### Event: `d3d_beginscene`

Event raised when the game client is beginning a new scene.

{{% expand "Click for more event information.." %}}
```lua
hook.events.registered('d3d_beginscene', 'd3d_beginscene_cb', function ()
end);
```

| Argument Name | Type | Description |
| --- | --- | --- |
| _None._ | --- | --- |

---
{{% /expand %}}

### Event: `d3d_endscene`

Event raised when the game client is ending a scene.

{{% expand "Click for more event information.." %}}
```lua
hook.events.registered('d3d_endscene', 'd3d_endscene_cb', function ()
end);
```

| Argument Name | Type | Description |
| --- | --- | --- |
| _None._ | --- | --- |

---
{{% /expand %}}

### Event: `d3d_present`

Event raised when the game client is presenting the scene.

{{% expand "Click for more event information.." %}}
```lua
hook.events.registered('d3d_present', 'd3d_present_cb', function ()
end);
```

| Argument Name | Type | Description |
| --- | --- | --- |
| _None._ | --- | --- |

---
{{% /expand %}}

### Event: `d3d_renderstate`

Event raised when the game client is setting a render state.

{{% expand "Click for more event information.." %}}
```lua
hook.events.registered('d3d_renderstate', 'd3d_renderstate_cb', function (e)
end);
```

| Argument Name | Type | Description |
| --- | --- | --- |
| `e.state`     | _number_  | `[Read Only]` The render state id. |
| `e.value`     | _number_  | The render state value. |
| `e.blocked`   | _boolean_ | Flag that states if the event has been blocked by daochook or another addon. |

---
{{% /expand %}}

### Event: `d3d_dip`

Event raised when the game client is about to render a primitive.

{{% expand "Click for more event information.." %}}
```lua
hook.events.registered('d3d_dip', 'd3d_dip_cb', function (e)
end);
```

| Argument Name | Type | Description |
| --- | --- | --- |
| `e.primitive_type`    | _number_  | `[Read Only]` The primitive type. |
| `e.base_vertex_index` | _number_  | `[Read Only]` The primitive base vertex index. |
| `e.min_index`         | _number_  | `[Read Only]` The primitive min index. |
| `e.num_vertices`      | _number_  | `[Read Only]` The primitive num vertices. |
| `e.start_index`       | _number_  | `[Read Only]` The primitive start index. |
| `e.prim_count`        | _number_  | `[Read Only]` The primitive primitive count. |
| `e.blocked`           | _boolean_ | Flag that states if the event has been blocked by daochook or another addon. |

---
{{% /expand %}}

### Event: `d3d_dipup`

Event raised when the game client is about to render a primitive.

{{% expand "Click for more event information.." %}}
```lua
hook.events.registered('d3d_dipup', 'd3d_dipup_cb', function (e)
end);
```

| Argument Name | Type | Description |
| --- | --- | --- |
| `e.primitive_type`            | _number_  | `[Read Only]` The primitive type. |
| `e.min_vertex_index`          | _number_  | `[Read Only]` The primitive min vertex index. |
| `e.num_vertex_indices`        | _number_  | `[Read Only]` The primitive num vertex indices. |
| `e.primitive_count`           | _number_  | `[Read Only]` The primitive primitive count. |
| `e.index_data`                | _number_  | `[Read Only]` The primitive index data. |
| `e.index_data_format`         | _number_  | `[Read Only]` The primitive index data format. |
| `e.vertex_stream_zero_data`   | _number_  | `[Read Only]` The primitive vertex stream zero data. |
| `e.vertex_stream_zero_stride` | _number_  | `[Read Only]` The primitive vertex stream zero stride. |
| `e.blocked`                   | _boolean_ | Flag that states if the event has been blocked by daochook or another addon. |

---
{{% /expand %}}

### Event: `d3d_dp`

Event raised when the game client is about to render a primitive.

{{% expand "Click for more event information.." %}}
```lua
hook.events.registered('d3d_dp', 'd3d_dp_cb', function (e)
end);
```

| Argument Name | Type | Description |
| --- | --- | --- |
| `e.primitive_type`    | _number_  | `[Read Only]` The primitive type. |
| `e.start_vertex`      | _number_  | `[Read Only]` The primitive start vertex. |
| `e.primitive_count`   | _number_  | `[Read Only]` The primitive count. |
| `e.blocked`           | _boolean_ | Flag that states if the event has been blocked by daochook or another addon. |

---
{{% /expand %}}

### Event: `d3d_dpup`

Event raised when the game client is about to render a primitive.

{{% expand "Click for more event information.." %}}
```lua
hook.events.registered('d3d_dpup', 'd3d_dpup_cb', function (e)
end);
```

| Argument Name | Type | Description |
| --- | --- | --- |
| `e.primitive_type`            | _number_  | `[Read Only]` The primitive type. |
| `e.primitive_count`           | _number_  | `[Read Only]` The primitive count. |
| `e.vertex_stream_zero_data`   | _number_  | `[Read Only]` The primitive vertex stream zero data. |
| `e.vertex_stream_zero_stride` | _number_  | `[Read Only]` The primitive vertex stream zero stride. |
| `e.blocked`                   | _boolean_ | Flag that states if the event has been blocked by daochook or another addon. |

---
{{% /expand %}}
