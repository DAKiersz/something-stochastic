# Powershell DSC - General Notes

## PSDesiredStateConfiguration Module

With release of Powershell 7.2, **PSDesiredStateConfiguration** is no longer included in Powershell Core. You can install **PSDesiredStateConfiguration** (DSC 2.0) from Powershell Gallery.

```Powershell
Install-Module -Name PSDesiredStateConfiguration -Repository PSGallery -MaximumVersion 2.99 -MinimumVersion 2.05
```

(With DSC 1.1 and Windows Powershell, this module is built-in)

Main: https://learn.microsoft.com/en-us/powershell/dsc/overview?view=dsc-2.0

Starting with version 2.0, DSC doesn't support applying configuration documents **directly** or running in **Windows PowerShell**. Instead, you must use the [Invoke-DscResource](https://learn.microsoft.com/en-us/powershell/module/PSDesiredStateConfiguration/Invoke-DscResource) cmdlet in PowerShell 7.2 or later to call the methods of a DSC resource.

Getting Started (DSC 2.0): https://learn.microsoft.com/en-us/powershell/dsc/getting-started/invoking-dsc-resources?view=dsc-2.0

## Resources - How to use?

Every DSC Resource has a schema to use the resource in one of two ways:

* Configuration blocks and `Import-DSCResource`, where the latter commandlet is exclusive to`Configuration` blocks. 
	* Main method.
	* A special kind of script, **and a standard in DSC 1.1**.
	* There are analogous to Ansible playbooks, but with Powershell syntax.
	* Use a declarative format.

* `Invoke-DscResource` can be used in the standard Powershell Core scripts. 
	* Only for DSC 2.0, and became non-experimental since DSC 2.0.6.
	* These can be integrated as part of your normal Powershell script.

Resources (DSC 2.0): https://learn.microsoft.com/en-us/powershell/dsc/concepts/resources?view=dsc-2.0

### Using Invoke-DscResource (DSC 2.0 Only)

```Powershell
Invoke-DscResource -Name Environment -Module PSDscResources -Method Set -Property @{
    Name   = 'DSC_EXAMPLE'
    Ensure = 'Present'
    Value  = 'Desired State Configuration'
    Target = 'Process'
}
```

* Name is the resource to use.
* Module is the resource module.
* Methods define what to do, or get from a resources. 
* Properties define details of a resource configuration element.

Methods: https://learn.microsoft.com/en-us/powershell/dsc/resources/get-test-set?view=dsc-1.1&source=recommendations

Example: https://learn.microsoft.com/en-us/powershell/dsc/reference/psdscresources/resources/windowsfeature/example?view=dsc-2.0

