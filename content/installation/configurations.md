---
title: "Configuring daochook"
weight: 4
---

Once **daochook** is fully and properly installed, you are ready to begin configurations.

### Launching daochook

**daochook** expects a boot configuration file to be passed to its launcher when running, such as:

```
daochook.exe atom0s.ini
```

When the launcher starts, it will take the given file name and locate it within the boot configuration directory automatically.\
The path to the **daochook** boot configuration directory is: `<Path To daochook>\config\boot\`

You can create multiple _(as many as you want)_ configuration files for each character you wish to play on, or per-server if you wish to not use the auto-login functionality.

### Boot Configuration File Format

The boot configuration file holds all of the information needed to launch the game client with **daochook** injected. It also includes some additional configurations used with **daochook** internally, such as if you wish to enable/disable certain included patches. Please read the following information carefully to ensure your boot configuration file is written correctly.

##### Section: `[import]` (optional)

  - `import` _(string)_ - The name of another boot configuration file to import. Merges the two files settings' together to form a single file.

The import section is an optional feature that allows advanced users to create base configuration files that can be used by multiple boot configurations. You can create a single base file that defines the `daochook.game`, `daochook.server` and `daochook.patches` sections then include that into each configuration that will use the same base information. Then your actual boot configuration file only needs to implement the `daochook.auth` for each character instead.

##### Section: `[daochook.game]`

  - `path` _(string)_ - The full path to your Dark Age of Camelot installation `game.dll` file that you wish to launch with **daochook**.

##### Section: `[daochook.server]`

  - `addr` _(string)_ - The server IP address (or DNS name) that you wish to connect to.
  - `port` _(number)_ - The server port that you wish to connect to.
  - `id` _(number)_ - The server id that you wish to connect to. _(Set to 42 if playing on a private server unless otherwise noted.)_

##### Section: `[daochook.auth]`

  - `username` _(string)_ - The username of the account you wish to login into.
  - `password` _(string)_ - The password of the account you wish to login into.
  - `character` _(string, optional)_ - The name of the character you wish to auto-log into.
  - `realm` _(string, optional)_ - The realm id of the character you wish to auto-log into. (0 = Albion, 1 = Hibernia, 2 = Midgard)

##### Section: `[daochook.patches]`

  - `disable_encryption` _(boolean)_ - Patch that will remove the packet encryption if enabled.
  - `disable_multi_instance_check` _(boolean)_ - Patch that will remove the multi-client instance check if enabled.

### Example Boot Configuration File

Here is a full example configuration file:

`<Path To daochook>\boot\config\atom0s.ini`:
```ini
[daochook.game]
path= Z:\Games\Electronic Arts\Dark Age of Camelot\game.dll

[daochook.server]
addr= 192.168.1.100
port= 10300
id= 42

[daochook.auth]
username= atom0s
password= password
character= Atomos
realm= 2

[daochook.patches]
disable_encryption = 1
disable_multi_instance_check = 1
```

### Import Usage Example

As mentioned above, advanced users can make use of the `import` section of the configuration file to include a base configuration file that holds information that would otherwise be duplicated across multiple files. Here is quick exmaple of using the `import` section for two characters that would connect to the same server.

`<Path To daochook>\boot\config\my_server.ini`:
```ini
[daochook.game]
path= Z:\Games\Electronic Arts\Dark Age of Camelot\game.dll

[daochook.server]
addr= 192.168.1.100
port= 10300
id= 42

[daochook.patches]
disable_encryption = 1
disable_multi_instance_check = 1
```

`<Path To daochook>\boot\config\atom0s1.ini`:
```ini
[import]
import=my_server.ini

[daochook.auth]
username= atom0s1
password= password
character= Atomosone
realm= 2
```

`<Path To daochook>\boot\config\atom0s2.ini`:
```ini
[import]
import=my_server.ini

[daochook.auth]
username= atom0s2
password= password
character= Atomostwo
realm= 2
```
