# Powershell DSC 1.1 - Configuration Blocks

## Example

```powershell
Configuration InstallHyperV {
	Import-DscResource -ModuleName PSDscResources
	   Node 'localhost' {   
	        WindowsOptionalFeature hyperv {
                Name =  "Microsoft-Hyper-V-All"
                Ensure = "Present"
			}
        }    
}
```

To compile, and execute the configuration:

```
.\config.ps1
Test-DscConfiguration -Path .
Start-DscConfiguration -Path "." -Wait -Force -Verbose
Get-DscConfigurationStatus
```
