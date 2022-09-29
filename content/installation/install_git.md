---
title: "Install via Git (Recommended)"
weight: 2
---

{{% notice info %}}
If you are unsure of using Git or do not wish to use it, then you can instead follow the instructions for downloading the latest release package manually as a .zip file. See [Install via Zip](/installation/install_zip/) instead.
{{% /notice %}}

Currently, the best, and recommended, way to install **daochook** is by using Git. You can either use Git via the command line or install your personal favorite Git client or shell integration. _There is no 'best' client or means of using Git, that is entirely personal choice on which you prefer to use._

Some recommended free solutions are:

  - Git For Windows _(Direct Git command line access.)_ - [https://git-scm.com/download/win](https://git-scm.com/download/win)
  - TortoiseGit _(Windows shell integration.)_ - [https://tortoisegit.org/](https://tortoisegit.org/)
  - GitHub Desktop _(Git GUI client.)_ - [https://desktop.github.com/](https://desktop.github.com/)
  - Sourcetree _(Git GUI client.)_ - [https://www.sourcetreeapp.com/](https://www.sourcetreeapp.com/)

By using Git, it is much easier to keep **daochook** up to date. You can simply pull the latest changes after you've initially cloned the release repository.

### Picking An Installation Folder

When picking a folder to install **daochook** to, it is important that you are **NOT** breaking the following guidelines.

{{% notice warning %}}
**daochook** should **NOT** be installed into a system protected folder.\
\
This means it should not be put into folders (or folders within) such as:\
`C:\Program Files (x86)\`, `C:\Program Files\`, `C:\Windows\`
{{% /notice %}}

{{% notice warning %}}
**daochook** should **NOT** be installed into the game client folder!\
\
You should never install **daochook** into the game client folder for safety reasons.\
It should be in its own separate folder entirely!
{{% /notice %}}

A recommended and safe installation location would be something such as:

  - `C:\daochook\`
  - `C:\Users\Your_Username_Here\Desktop\daochook\`
  - `Z:\Some\Other\Folder\daochook\`

### Cloning The Release Repository

Please note, because there are so many different Git clients available, it is not possible for us to write a full guide for each one. Instead, this guide will demonstrate how to install using two preselected UI clients and with Git via the command line. The two clients that this guide will use are `GitHub Desktop` and `TortoiseGit`.

#### Installing via `GitHub Desktop`

1. First, download and install the `GitHub Desktop` client. Once installed, launch it and either sign in with your existing GitHub account, or skip the sign in step. _(**Note**: You do not need to sign in to clone the **daochook** repository, so you can skip the sign in step if you do not want to or do not wish to create an account with GitHub.)_
2. From the top menu, click `File` then `Clone Repository...`
3. In the clone window, click the `URL` tab at the top, then enter the repository URL: `https://github.com/daochook/daochook.git` For the local path, ensure you follow the guidelines above and place `daochook` into a valid path. For example, `C:\daochook`
4. Click `Clone`.

If everything was successful, you're done and should have **daochook** now installed to the selected folder!

#### Installing via `TortoiseGit`

1. First, download and install `Git for Windows` and `TortoiseGit`. Follow the various prompts to fully install both tools.
2. Restart your computer. _(This is recommended as `TortoiseGit` is a shell extension.)_
3. Navigate to the parent folder where you plan to install **daochook** to. For example: `C:\`
4. Right-click within the parent folder and choose `Git Clone..` _(Be sure you are not right-clicking on a folder!)_
5. In the clone window, enter the repository URL: `https://github.com/daochook/daochook.git` For the `Directory` ensure the path is correct and that it has automatically added `\daochook` to your parent folder.
6. Click `OK` to clone.

If everything was successful, a second window should show with some information about the clone and that it was successful. If so, then you're done and should have **daochook** now installed to the selected folder!

#### Installing via `Git Command Line`

1. First, download and install `Git for Windows`. Follow the various prompts to fully install.
2. Open a new command prompt window. _(cmd, powershell, Windows terminal, bash, etc. are all suitable for this.)_
3. Navigate the command prompt to the parent folder you wish to install **daochook** to. For example: `cd C:\`
4. Enter the following command: `git clone https://github.com/daochook/daochook.git`

If everything was successful, you're done and should have **daochook** now installed to the selected folder!