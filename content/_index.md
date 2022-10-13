---
title: "Index"
---

![daochook](./images/daochook.png?width=64px)
# daochook

{{% button href="https://discord.gg/mkfP3XkZZ2" icon="fa-brands fa-discord" %}}Discord Chat{{% /button %}}
{{% button href="https://github.com/daochook/daochook" icon="fa-brands fa-github" %}}GitHub Repo{{% /button %}}
{{% button href="https://github.com/daochook/daochook/issues" icon="fa-brands fa-github" %}}Bug Reports{{% /button %}}
{{% button href="https://daochook.github.io/" icon="fa-solid fa-book" %}}Documentation{{% /button %}}

### What is `daochook`?

**daochook** is a free feature-rich third-party enhancement/modification for the MMORPG, Dark Age of Camelot.\
_(See the features page for a full list of **daochook's** features.)_

### Support My Work

Want to say thanks for **daochook**? Feel free to donate or sponsor me on the following platforms.

{{% button href="https://github.com/atom0s" icon="fa-brands fa-github" %}}Sponsor via GitHub{{% /button %}}
{{% button href="https://patreon.com/atom0s" icon="fa-brands fa-patreon" %}}Sponsor via Patreon{{% /button %}}
{{% button href="https://www.paypal.me/atom0s" icon="fa-brands fa-paypal" %}}Donate via PayPal{{% /button %}}

{{% notice note %}}
**daochook** is released completely free of charge.\
Donations and sponsorships are completely optional and are a means to say thanks.
{{% /notice %}}

### How does `daochook` work?

**daochook** is an injected hook that is directly injected into the DAoC game client (`game.dll`) while launching the game.

Because of how **daochook** functions, it works entirely separate from the games files and _**DOES NOT**_ require any additional client modifications! You do not need to modify any of your existing client files in order to use **daochook** making setup and usage a breeze.

Once injected into the game client, **daochook** then hooks itself onto several game functions allowing it to both take control of said functions, but also allow Lua addons to inject various things into the client as if it was done normally by the player.

For example, **daochook** hooks onto the games chat input where you would normally enter a command such as `/wave` to wave at someone. **daochook** intercepts all commands that run through the games command interpreter/handler and forwards them to its custom Lua addon engine. Addons can then decide if the command should be blocked from executing, allowing an addon to react to it first. This setup allows addons to implement and react to custom commands that are otherwise not built into the game client.

Along with this, by hooking the command handler function, Lua addons can also inject commands as if the player typed them, used a macro, or any other means of input the client would normally recognize.

This approach is applied for several major game functions allowing **daochook** to greatly enhance the features of the client.