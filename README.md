<div align="center">
    <img width="128" src="https://github.com/daochook/daochook.github.io/raw/main/static/images/daochook.png" alt="daochook">
    <br/>
</div>

<div align="center">
    <a href="https://discord.gg/mkfP3XkZZ2"><img src="https://img.shields.io/discord/1022736642257211393.svg?style=for-the-badge" alt="Discord server" /></a>
    <a href="LICENSE.md"><img src="https://img.shields.io/badge/License-AGPL_v3-blue?style=for-the-badge" alt="license" /></a>
    <br/>
</div>

**daochook** is a free feature-rich third-party enhancement/modification for the MMORPG, Dark Age of Camelot.

## Donations & Sponsorships

daochook is released completely free of charge. You can say thanks by donating or via sponsorships.

  * **GitHub Sponsor:** https://github.com/sponsors/atom0s
  * **Patreon Sponsor:** https://patreon.com/atom0s
  * **PayPal Donation:** https://www.paypal.me/atom0s

## Documentation Requirements

In order to work on the documentation, you must have `hugo` installed.

You can find more information on how to install `hugo` here:
[Click Here](https://gohugo.io/getting-started/installing/)

## Building Documentation Locally

Once you have `hugo` installed, you can build and view the documentation offline / locally by running `hugo` via:

```
cd /path/to/documentation
hugo server
```

Once `hugo` is running it will display a url you can visit to view the documentation locally. `hugo` will also live update any changes you make to the documentation. _(In some cases, you may need to terminate `hugo` and run it again for full changes to take affect.)_

## Documentation Theme

The documentation is using a theme called `learn`. However, the official release of this theme is outdated, thus a fork has been made to keep the third-party dependencies up to date manually. You can find our fork of the theme here: https://github.com/daochook/hugo-theme-learn

Any design changes that you wish to contribute should be done as an override in this repository. _Do not make theme edits/changes to the actual theme repo linked above!_

## Published Documentation Notes

The repository is setup with a custom GitHub workflow that will automatically rebuild the documentation and publish it. This workflow automatically creates and pushes the built website to the `gh-pages` branch within this repo. Please **DO NOT** edit the workflow file and **DO NOT** edit or commit anything to the `gh-pages` branch. This branch is automatically overwritten each time the website is rebuilt, so your changes will be lost!

## Legal

**daochook** does not claim ownership of any material(s) related to DAoC.

```
Dark Age of Camelot is copyright © 2021 Electronic Arts Inc.
All Rights Reserved.
```

Please note; the work done within **daochook** is done against private servers. **daochook** is not developed against live servers. The reverse engineering done by this repository and its contributors is entirely 'clean room'. We **DO NOT** have or use any leaked source code or other unpublished material. Any contributions made to **daochook** **MUST** adhere to the following requirements:

  * You are not employeed by EA, or have been previously, in any capacity.
  * You do not and have never had any leaked material from EA related to DAoC in any manner.
  * You do not and have never referenced any leaked or otherwise unreleased material from EA related to DAoC in any manner.

We **DO NOT** claim ownership of any material or information gathered through the means of reverse engineering the client and its files for this purpose.

## License

**daochook** is licensed under GNU AGPL v3

Please be sure you understand the license before making use of **daochook**. This is AGPL, not standard GPL.

## Credits

**daochook** is created and developed by [atom0s](https://github.com/atom0s).

For a full list of credits, please visit: [daochook Credits](https://daochook.github.io/credits)
