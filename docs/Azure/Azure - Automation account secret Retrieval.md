# Azure - Automation account secret retrieval

An example of retrieving passwords (secrets) from An Azure Automation Account 

```powershell
$secret1 = Get-AzAutomationCredential -Name "xxx"
$secret1 = $secret1.GetNetworkCredential().Password
```

## References

https://learn.microsoft.com/en-us/azure/automation/shared-resources/credentials?tabs=azure-powershell`