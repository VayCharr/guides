---
layout: post
title: Guild Wars 2 - Directing Steam to your standalone installation
asset_path: /assets/guides/2023-08-25-gw2-symlinks
categories: 
  - guides
---

# Using Directory Junctions

Using a Directory Junction, you can re-use the files you already have from your standalone GW2 installation on Steam. This works because the Steam version is a 1:1 copy of the standalone version (aside from some Steam-specific configuration files).

[mklink — Microsoft Documentation](https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/mklink)]

## Select Installation Location

Determine where you want your Guild Wars 2 Steam installation to be located. The folder structure typically looks like this:

```text
C:\Program Files (x86)\Steam\steamapps\common
```

Make sure there is no existing Guild Wars 2 folder within your Steam directory. If one exists, delete it to prevent any conflicts.

## Open Command Prompt as Administrator

1. Open the Windows Start menu.
2. Type "cmd".
3. Select "Run as administrator" to ensure you have the necessary permissions for the upcoming steps.

![Open command prompt as administrator]({{ page.asset_path }}/cmd_admin.png)

## Create a Directory Junction

Use `mklink` to create a Directory Junction that points your Guild Wars 2 Steam folder to the standalone folder. The `mklink` syntax is as follows:

```text
mklink /J <link> <target>
```

- Replace `<link>` with the path to your Steam Guild Wars 2 folder.
- Replace `<target>` with the location of your existing Guild Wars 2 installation folder.

For example:

```text
mklink /J "C:\Program Files (x86)\Steam\steamapps\common\Guild Wars 2" "C:\Your\Existing\Guild Wars 2\Folder"
```

![Example of a directory junction]({{ page.asset_path }}/directory_junction.png)

## Start Installation via Steam

After setting up the Directory Junction, proceed to install Guild Wars 2 through Steam by clicking "Install" on the game's page.

![Steam install button]({{ page.asset_path }}/steam_install_button.png)

## Launch Guild Wars 2 via Steam

Upon completion of the installation process, Steam will recognize the game as installed and immediately display it as playable in your library.

![Guild Wars 2 on Steam]({{ page.asset_path }}/gw2_install_steam.png)

## Using Your ArenaNet Account on Steam

To utilize your ArenaNet account instead of your Steam account, follow these steps:

## Access Guild Wars 2 Properties in Steam Library

1. Right-click on Guild Wars 2 within your Steam Library.
2. Select "Properties."

![Steam properties window]({{ page.asset_path }}/steam_properties_window.png)

## Navigate to Launch Options

1. In the Properties window, locate the "Launch Options" section.

## Add Launch Parameter

Add the following launch parameter within the Launch Options section:

```text
-provider Portal
```

![Steam properties window]({{ page.asset_path }}/steam_properties_window_2.png)

This parameter ensures that Guild Wars 2 will utilize your ArenaNet account for authentication instead of your Steam account.

## Using Gw2Launcher to Launch Through Steam

The popular open-source account managing tool, Gw2Launcher, supports launching accounts through Steam.

## General Settings

### Access Settings

1. Click on the menu icon located in the top-left corner of Gw2Launcher.
2. Select "Settings."

![GW2Launcher]({{ page.asset_path }}/gw2launcher_settings.png)

### Navigate to Guild Wars 2 Steam Settings

1. Within the Settings menu, navigate to the "Guild Wars 2" tab.
2. Click on "Steam."

![GW2Launcher]({{ page.asset_path }}/gw2launcher_settings_2.png)

### Adjust Steam Installation Location

If your Steam installation is not in the default directory, specify its location here.

### Configure Launch Behavior

Choose how Gw2Launcher should behave when launching multiple accounts through Steam.

## Account Settings

### Edit Account Details

1. Right-click on the account(s) you intend to launch via Steam within Gw2Launcher.
2. Select "Edit."

![GW2Launcher]({{ page.asset_path }}/gw2launcher_settings_3.png)

### Access Launch Options

1. In the account editing window, navigate to the "Launch options" section.

### Set Provider to ArenaNet

1. Ensure that "ArenaNet (Default)" is selected under the Provider dropdown menu.

### Enable Steam Launch

1. Check the box labeled "Launch through Steam" to enable launching via Steam for the selected account(s).

## Limitations

If Steam updates Guild Wars 2 without Gw2Launcher's awareness, launching the game may encounter issues. To resolve this, force-update the game by right-clicking on the affected account and selecting "update."

![GW2Launcher]({{ page.asset_path }}/gw2launcher_settings_4.png)
