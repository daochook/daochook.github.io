---
title: "Features"
weight: 10
disableToc: false
chapter: false
---

Because **daochook** is injected into the game client, it can hook onto the game in various ways. This allows for many features that are not generally possible with just external tools alone. Check out the various features of **daochook** below for more information.

### Custom Launcher (Injector)

**daochook** ships with its own basic command line injector/launcher. This is to ensure that **daochook** is injected properly and as soon as possible in the launching of the game client. _(Other injectors are supported as long as they are able to call exported functions.)_

{{%expand "Click to read more..." %}}
The included injector also allows for quick login access using any version of the client that supports it.

```cpp
// General Usage
daochook.exe [configname.ini]
```
{{% /expand%}}

### Injected Hook

As previously mentioned, **daochook** is injected directly into the game client (`game.dll`). This gives the project an advantage over other external third-party tools as it can directly access the games data, memory and functions.

**daochook** also hooks onto the games Direct3D device to allow for custom rendering and additional rendering related features. _(See below for more info.)_

### Hooked Game Functions

**daochook** takes advantage of being injected by hooking onto several major game functions including:

  - `(Chat) Command Handler` - _The game function responsible for handling all command input within the client. (Typed, macros, built-in system, menus, etc.)_
  - `(Chat) Message Handler` - _The game function responsible for outputting messages to the chat/combat log window(s)._
  - `(Packets) Incoming Packet Handler` - _The game function responsible for handling incoming packets from the server._
  - `(Packets) Outgoing Packet Handler` - _The game function responsible for handling outgoing packets from the client._

By hooking onto these functions, **daochook** is able to do multiple things including:

  - **Read:** See any time the function(s) are called and log/view the parameters they were called with.
  - **Block:** Prevent the game client from ever seeing the call was made.
  - **Modify:** Alter the parameters to change how the call will actually be invoked by the game client.
  - **Inject:** Manually invoke the original function to easily inject custom data.

{{%expand "Click to read more..." %}}
For example, let's look closer at the `(Chat) Command Handler` function. This function is responsible for handling all command input within the client. This function is called whenever the user types something into chat, uses a slash command (ie. `/wave`), presses a macro, clicks a button that will cause a command to be parsed/interpreted, etc.

The function looks like this:

```cpp
void handle_cmd(const char* command, int32_t mode)
{
    // ...
}
```

_The game client also has a secondary input mode pointer that is used with command input that is not passed as a normal argument, it is instead a global variable._

Any time a command is to be handled by the client it will pass through this function. Once hooked, **daochook** has the ability to fully take control of the function call. Each time the function is called, **daochook** will first attempt to 'handle' it. This means that the command will go through a 'process' chain to see if anything can make use of it before it eventually gets sent to the client to be handled as normal.

The order in which things happen looks like this:

  1. Game calls original command handler function.
  2. **daochook** intercepts the call, forwards it to its own internal handler.
  3. **daochook** checks for any built-in commands it will handle first. (ie. `/addon`)
      1. If **daochook** handles the command, it is blocked from being seen by the client.
      2. If **daochook** does not handle the command, the chain continues.
  4. **daochook** forwards the command to its internal addon manager.
  5. The addon manager sends the command to all loaded addons that have a valid `command` event handler registered.
      1. If an addon handles the command, it is blocked from being seen by the client.
      2. If no addon handles the command, the chain continues.
  6. If nothing has handled the command, it is sent to the client as normal.

During this chain, both **daochook** and/or an addon have the chance to alter any of the parameters of the original call. For example, if the command being handled is `/wave` and instead you want to do `/shrug`, you can easily do this with an addon.

_This can also be used to modify incoming and outgoing packets, or out-right block packets from being sent or received!_
{{% /expand%}}

![hook_1.gif](/features/images/hook_1.gif)

### Direct3D Hook

Along with hooking various game functions, **daochook** also hooks onto the games Direct3D device. This allows the hook to render its own things into the game scene, either in 2D or 3D. The main purpose for this however, is to allow the use of ImGui to render custom in-game UI elements from addons.

### Custom UI via ImGui

**daochook** implements and [fully] exposes ImGui to Lua for addons to make use of. You can easily create your own custom UI elements that can interact with the game directly, display useful / important game information, and much much more!

You can find more information about ImGui here: [https://github.com/ocornut/imgui](https://github.com/ocornut/imgui)


![imgui.gif](/features/images/imgui.gif)

### Addons, Powered By Lua!

**daochook** includes a powerful custom addon system, backed by Lua. _(LuaJIT to be more specific, via MoonJIT)_

Addons are sandboxed/isolated Lua scripts that can be used to greatly enhance the game play experience of the game. Addons can do a wide varity of things and are able to directly communicate with the game client in multiple ways.

You can access all of the hooked functions directly to allow your addon to easily inject commands, chat messages, packets and more.

Addons also have full access to ImGui, allowing you to create your own feature-rich UI's.

With the use of LuaJIT, addons also have access to C style structure definitions, casting, and function calling, allowing addons to even further extend their usefulness by directly interacting with game data and functions.

For example, here is a simple addon that will handle the command `/derp`. Anytime this command is used, it will instead use `/wave`.

```lua
addon.name    = 'example';
addon.author  = 'atom0s';
addon.desc    = 'A simple example addon.';
addon.link    = 'https://atom0s.com';
addon.version = '1.0';

require 'common';
require 'daoc';

hook.events.register('command', 'command_cb', function (e)
    -- Parse the command into arguments..
    local args = e.modified_command:args();

    -- Command: /derp
    if (#args >= 1 and (args[1]:ieq('derp') and e.imode == daoc.chat.input_mode.slash) or args[1]:ieq('/derp')) then
        -- Mark the command as handled, prevents the game from seeing it..
        e.blocked = true;

        -- Inject a new command into the handler..
        daoc.chat.exec(daoc.chat.command_mode.typed, daoc.chat.input_mode.normal, '/wave');
        return;
    end
end);
```

_For full information on addons, please check the developer documentation section of this site!_

### Window Modifications

**daochook** modify the game window such that the icon is shown and overridden with the projects own icon. The window title is also automatically updated to your current characters name to make finding the proper game window when multiboxing much easier. It also allows third-party programs to interact with the game windows much easier as you can just use the window name to find the proper process if you are using certain older tools.

![window_1.png](/features/images/window_1.png)
![window_2.png](/features/images/window_2.png)