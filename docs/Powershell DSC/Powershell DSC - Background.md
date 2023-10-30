# Powershell DSC - Background

## Summary

Powershell DSC is essentially a configuration management tool, originally aimed at configuring Windows machines. There is an ongoing effort to make this tool OS-agnostic.

Powershell DSC is a Powershell Module that can be used to invoke DSC Resources, the elements of configuration equivalent to Ansible tasks.

At the time of writing (October 2023) the main version is 2.0.7. **However, version 1.1 is still used if you are not using Azure Automanage machine configuration feature.**

Powershell Docs: https://learn.microsoft.com/en-us/powershell/scripting/dsc/overview?view=powershell-7.3

Main Docs (DSC v2.0): https://learn.microsoft.com/en-us/powershell/dsc/overview?view=dsc-2.0

Main Docs (DSC v1.1) https://learn.microsoft.com/en-us/powershell/dsc/overview?view=dsc-1.1 

## DSC Resources

**DSC Resources** provide a standardsed interface for managing the settings of a system. They define system properties that can me managed (i.e., configurable elements).

To use Powershell DSC we must also install and use additional **modules** containing a set of related DSC resources, atop of the `PSDesiredStateConfiguration` i.e., DSC, module. 

Resources (2.0): https://learn.microsoft.com/en-us/powershell/dsc/concepts/resources?view=dsc-2.0

You can find DSC resource modules:

```powershell
Find-DscResource -Repository PSGallery | Select-Object -Property ModuleName, Version -Unique
```

You can install these as you would with any Powershell module:

```powershell
Install-Module 'PSDscResources' -Repository PSGallery -Force -AcceptLicense
```

You can check resource syntax after installing a module containing it:

```
Get-DscResource -Syntax WindowsFeature
```

Typing in `Get-DscResource` lists all resources available on to Powershell context.

Getting Started: https://learn.microsoft.com/en-us/powershell/dsc/getting-started/invoking-dsc-resources?view=dsc-2.0

