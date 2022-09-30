---
title: "Developers"
---

**daochook** allows anyone to further expand on its features through its custom addon system. Addons are powered by Lua _(more specifically, LuaJIT via MoonJIT)_.

### What is Lua?

Lua is a powerful, fast and lightweight scripting language that can be embedded into nearly any kind of project.

Lua combines simple procedural syntax with powerful data description constructs based on associative arrays and extensible semantics. Lua is dynamically typed, runs by interpreting bytecode for a register-based virtual machine, and has automatic memory management with incremental garbage collection, making it ideal for configuration, scripting, and rapid prototyping.

**daochook** makes use of LuaJIT, via the fork called MoonJIT. You can find more information about each of these projects here:

  - **Lua**: http://www.lua.org/about.html
  - **LuaJIT**: https://luajit.org/
  - **MoonJIT**: https://github.com/moonjit/moonjit

### What are addons?

Addons are individual isolated/sandboxed instances of a Lua state that loads/runs a given base Lua script. This script will remain loaded until it either is manually unloaded by the player or told to unload otherwise by other means. _(ie. If another addon tells it to unload, or it has an error etc.)_ Addons generally function by registering to predefined events exposed by **daochook** which allows them to react to various things. An addon can also do something as simple as patching part of the game client when it loads and then nothing else for the duration that it is loaded.

Because addons have the potential to throw an error, they are ran in isolated/sandboxed instances of Lua. This means that every loaded addon has its own Lua state. Addons are considered 'dumb' in the sense that they are not aware of another addon being loaded/existing because of this sandboxed setup. If an addon throws an error, instead of causing all addons to stop working, it simply causes only the single addon that errored to stop.

**daochook** exposes a large amount of helpful functions to each addon that implements various things such as:

  - Access to certain game functions.
  - Access to game memory through read/write helpers.
  - Access to additional file IO helpers.
  - Access to additional regex helpers.
  - Access to additional time related helpers.
  - And more!

Since **daochook** is also using LuaJIT, addons have access to its FFI library, which even further greatly expands on the features that addons can make use of. FFI, which stands for foreign function interface, allows you to make use of calling external C functions, using C data structures, and casting direct memory to function definitions / memory structures all from within Lua. This greatly enhances what can be done from an addon.

### How do addons work?

As mentioned above, addons run isolated in their own Lua state. Once an addon is loaded, any time a predefined event occurs within **daochook**, the event will then be forwarded and raised in all loaded addons that have registered to the given event.

For example, an event that **daochook** exposes is `command`. This event is raised any time the game client is attempting to process a command that was sent to the games internal command handler. _(ie. When typing into the chat box, using a 'slash' command such as `/wave`, using a macro, etc.)_

When the event is raised, it will be passed to **daochook**'s internal addon manager, which then loops through all loaded addons, and raises the event inside each addon that has a valid registered event callback for the event. _Addons can register to an event multiple times if needed as well._

These events allow addons to react to various aspects of the game.

### Additional Lua Information

Whether you are new to Lua or a seasoned pro, here are some links to help get you started or freshen up on your Lua knowledge.

#### Lua Project Links

  - **Lua Manual 5.1:** http://www.lua.org/manual/5.1/
  - **Lua Manual 5.2:** http://www.lua.org/manual/5.2/
  - **Lua Manual 5.3:** http://www.lua.org/manual/5.3/
    - _**Note:** MoonJIT, which is used within **daochook** implements LuaJIT with parts of Lua 5.2 and 5.3 added. Not all features of 5.2/5.3 are available though._
  - **Programming In Lua (EBook):** http://www.lua.org/pil/contents.html
  - **Lua Wiki:** http://lua-users.org/wiki/
  - **Lua Wiki Tutorial List:** http://lua-users.org/wiki/TutorialDirectory
  - **Lua Mailing List:** http://www.lua.org/lua-l.html
  - **Lua Forums:** https://luaforum.com/index.php

#### Lua Tips and Tricks / Performance Information

  - http://www.lua.org/gems/sample.pdf
  - http://lua-users.org/wiki/OptimisationTips
  - https://web.archive.org/web/20100609035807/https://stackoverflow.com/questions/89523/lua-patterns-tips-and-tricks
  - https://stackoverflow.com/questions/154672/what-can-i-do-to-increase-the-performance-of-a-lua-program/12865406#12865406

#### Metatables

  - http://www.lua.org/pil/13.html
  - http://phrogz.net/lua/LearningLua_MetatableEvents.html
  - http://phrogz.net/lua/LearningLua_ValuesAndMetatables.html
  - http://www.dreamincode.net/forums/topic/175747-lua-metatables-tutorial/

#### Examples / Tutorials

  - http://lua-users.org/wiki/SampleCode
  - http://lua-users.org/wiki/TutorialDirectory
