---
title: "Features"
weight: 10
disableToc: false
chapter: false
---

![daochook](./../images/daochook.png?width=64px)

**daochook** offers an enhanced player experience by providing a feature-rich platform to work from. Below you can find an overview of the projects main features. _Please note, because **daochook** offers a very in-depth Lua addon interface, the feature-set of the project is endless and ever-expanding by users sharing addons!_

### Custom Injector / Launcher

**daochook** ships with its own command line injector/launcher. This allows the project to ensure it is properly launched, injected and ran as expected. The launcher is designed to be easy to use and understand by anyone. The launcher also supports two forms of injecting into the game client.

  - By injecting into a new process. _(Launched by the injector itself.)_
  - By injecting into an existing process.

_You may use another injector/launcher if you wish, however that launcher must properly invoke **daochook**'s installation export function. If you are working on a custom injector for **daochook** and need help with this, please contact `atom0s` on the Discord server._

{{%expand "Click to read more..." %}}
The included injector also allows for quick login access using any version of the client that supports it.

```cpp
// General Usage - (Create a new game process and inject..)
daochook.exe <config_name.ini>

// Advanced Usage - (Inject into an existing game process..)
daochook.exe <config_name.ini> [process_id]

// Examples
daochook.exe atom0s.ini
daochook.exe atom0s.ini 1234
```
{{% /expand%}}

### Injected Hook

**daochook** operates by being directly injected into the game client (`game.dll`) process. This gives the project several advantages over standard external third-party tools. By being directly injected, **daochook** can directly access the games memory, functions, and other data. It can also easily hook and/or patch the game client in various ways. **daochook** makes use of this by hooking onto several game functions to greatly enhance the client and expose information to addons. _(See more information below!)_

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

Along with hooking various game functions, **daochook** also hooks onto the games Direct3D device. This allows the hook to render its own things into the game scene, either in 2D or 3D. The main purpose for this however, is to allow the use of ImGui to render custom in-game UI elements from addons. By hooking the Direct3D interface, it is also possible to alter how the scene renders, helping clean up visibility in various conditions.

#### Toggling The Game Fog Rendering

![d3d_fog.png](/features/images/d3d_fog.png)

_The games fog can be toggled on and off with a simple slash command._

#### Altering The Game Ambient Light Rendering

![d3d_ambient.png](/features/images/d3d_ambient.png)

_The games ambient lighting can be toggled on and off, and overridden with a custom color allowing you to see easier in the dark or if your system has a hard time displaying darker areas._

#### Toggling The Z-Buffer Rendering

![d3d_zbuffer.png](/features/images/d3d_zbuffer.png)

_The game z-buffer can be toggled on and off with a simple slash command, making it possible to see through walls._ _(**Note:** This does not allow you to target or cast through walls! Collision and obstruction still works as normal.)_

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

**daochook** modifies the game window such that the icon is shown and overridden with the projects own icon. The window title is also automatically updated to your current characters name to make finding the proper game window when multiboxing much easier. _It also allows third-party programs to interact with the game windows much easier as you can just use the window name to find the proper process if you are using certain older tools._

#### Custom Window Title Override

![window_title.gif](/features/images/window_title.gif)

#### Custom Window Icon Override

_Overridding the window icon and taskbar icons.._
![window_icon1.png](/features/images/window_icon1.png)

_Overridding the ALT+Tab window icon.._

![window_icon2.png](/features/images/window_icon2.png)

### Custom `user.dat` Override Fix

Long time players will know the bug dealing with the `user.dat` file and all the headaches it can cause. Crashing while multiboxing can lead to tons of undesired downtime due to having to micro-manage numerous accounts after a crash. **daochook** includes a custom patch/fix for this problem. When enabled, **daochook** will override the path that the game attempts to look for your `user.dat` file, making it individual per-account. This means that each account can easily have its own settings without interferring with another client.

These custom overrides are stored in: `<daochook_path>\config\daoc\<account_name>\user.dat`

_You can easily copy your existing user.dat file(s) into the proper folders based on your account names or allow the client to create a new one for each account you log into with this setting turned on._

No longer do you need to juggle accounts after one crashes to avoid losing all your characters settings!
