# Terraform - With Azure

## Providers

In `providers.tf`, we should use the following two providers:

```
terraform {
  required_providers {
    azurerm = {
      source  = "hashicorp/azurerm"
      version = ">=3.0.1"
    }
    azapi = {
      source = "Azure/azapi"
    }
  }
}
```

* `azurerm` is the official provider from Hashicorp for deploying Azure Resources.
* `azapi` is a thin wrapper around Azure Resource Manager (ARM) API.

## Tools

### aztfexport

https://github.com/Azure/aztfexport

"A tool to bring your existing Azure resources under the management of Terraform"

Export a single resource by its Azure full `\_ResourceID`:

`aztfexport resource [option] <resource id>` 

Export a resource **group** and its including resources by its name:

`aztfexport resource-group [option] <resource group name>` 

### aztft

https://github.com/magodo/aztft

"A CLI tool (and a library) to query for the AzureRM Terraform Provider resource type based on the input `\_ResourceID`.""

i.e., Import Azure \_ResourceID --> AzureRM Terraform Provider 

### Azure Backend

https://developer.hashicorp.com/terraform/language/settings/backends/azurerm 

A way to remotely store state files in a storage account (via Azure Blob Storage).
