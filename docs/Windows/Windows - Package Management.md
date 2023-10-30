---
title: Windows - Package Management
date: 2023-10-12T14:02:00
tags:
  - Windows
  - Automation
---
## Winget

A package manager for Windows, akin to `apt` in Debian based Linux distros.

To find a package:

`winget search [package]`

And to install, with a **exact** option.

`winget install [packageid] -e`

To list installed packages on the system:

`winget list`

You can export configuration, and specify the source:

`winget export -s winget -o ./export.json`

and import your config to a new machine:

`winget import -i export.json`

## AppxPackage

This is a PowerShell module for managing MSIX and AppX packages, which can be used to remove bloatware.

https://learn.microsoft.com/en-us/powershell/module/appx/get-appxpackage?view=windowsserver2022-ps

To install `package`, for example (note, this needs to be downloaded):

`Add-AppxPackage -Name 'Package'`

List packages currently installed:

`Get-AppxPackage | Select-Object Name, Version`