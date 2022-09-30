---
title: "Creating Addons"
pre: "1. "
weight: 1
---

{{% notice warning %}}
Failure to follow the directions given here will result in your addon most likely not loading or immediately crashing/erroring. Addons are expected to follow a strict layout / guideline in order to be able to load and function properly! Be sure to read carefully before asking for help.
{{% /notice %}}

### Creating A New Addon

Addons are located within the `<Path To daochook>\addons\` directory. Inside of this folder, you will see individual folders for each addon, as well as a `libs` folder which contains a handful of helper libraries that addons can make use of while running.

Please be sure that you understand the following:

  - Addons **MUST** have their own individual folder.
  - Addons **MUST** have their main `.lua` script file named the same thing as their folder.

For example, if you wanted to make an addon named 'hello', you would make the following:

  - `<Path To daochook>\addons\hello\` _(The addon folder.)_
  - `<Path To daochook>\addons\hello\hello.lua` _(The addons main `.lua` file.)_

The name of the folder and main `.lua` file for each addon is the name that is also used for any of the in-game `/addon` commands.

Failure to follow this setup will result in your addon not loading.

### Coding Addons With VSCode

Lua is coded in plain-text script files with the `.lua` extension. There are many code editors that support the Lua language syntax, however we recommend that you use Visual Studio Code. VSCode has multiple extensions that support and extend the Lua syntax. Below is a list of links to the various extensions we recommend you use while developing addons.

  - **VSCode**: https://code.visualstudio.com/
  - **sumneko.lua**: https://marketplace.visualstudio.com/items?itemName=sumneko.lua

Once installed, you can open the addons folder in VSCode _(File -> Open Folder)_ to have the Lua extension pick up the included predefined information found in the `/addons/.vscode/settings.json` file. This file holds predefined globals information to help the plugin understand types that are not directly defined in any of the included `libs` files. _(ie. Things exposed by **daochook**)_ It is recommended that anytime you are editing an addon, that you open the entire addon folder like this to allow the extension to load these settings. Failure to do so may result in the editor showing errors/warnings on various parts of your code that are otherwise valid.

### Coding Your Addon

Once you have your environment setup and established, open your new addon's main `.lua` script in your preferred editor. _(Again, if you are using VSCode, you should open the entire addons folder while editing your addon!)_

At the top of your file, it is recommended to include a license which states how you wish to share your code. Lua scripts are open source by design, so you will need to understand regardless of what license you pick, anyone that you share the addon with will be able to see its code directly. Feel free to check out the included example addons, libs, etc. for how the license should look. **daochook** is released under the GNU AGPL v3 license. Other common licenses for open source files are: Apache, BSD, GNU GPL v2, GNU GPL v3, MIT _(It is recommended that you read up on each license before picking one and ensuring you understand what it means.)_

Next, your addon **MUST** implement the expected `addon` table information. Failure to include this table in your addon will result in your addon not loading.

The `addon` table will look like this:

```
addon.name    = 'hello';
addon.author  = 'atom0s';
addon.desc    = 'An example addon.';
addon.link    = 'https://atom0s.com';
addon.version = '1.0';
```

For more information regarding the predefined `addon` table, please continue to the next documentation page: [Addon Table Information](/developers/addon_table/)
