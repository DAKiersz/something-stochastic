
# Azure - NewAzResourceGroupDeployment

Powershell cmdlet `New-AzResourceGroupDeployment`  allows you to deploy resources to a resource group from an ARM/Bicep Template

## Example

```powershell
New-AzResourceGroup -Name $resourceGroupName -Location "$location"
New-AzResourceGroupDeployment `
    -ResourceGroupName $resourceGroupName `
    -TemplateUri "https://raw.githubusercontent.com/Azure/azure-quickstart-templates/master/quickstarts/microsoft.compute/vm-simple-windows/azuredeploy.json" `
    -adminUsername $adminUsername `
    -adminPassword $adminPassword `
```