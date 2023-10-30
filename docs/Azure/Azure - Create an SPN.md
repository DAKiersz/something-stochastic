# Azure - Create an SPN

Create a Service Principal with Azure CLI

```shell
az ad sp create-for-rbac/
--name test-spn /
--role contributor /
--scopes /subscriptions/xxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxx
```

This returns:

```
  "appId": "xxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxx",
  "displayName": "test-spn",
  "password": "xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx",
  "tenant": "xxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxx"
```