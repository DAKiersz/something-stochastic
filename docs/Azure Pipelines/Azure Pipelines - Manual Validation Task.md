# Azure Pipelines - Manual Validation Task

This task runs on `pool: server` until manually approved.

```yaml
- task: ManualValidation@0
  inputs:
	notifyUsers: 
	instructuions:
	onTImeout: 
```

## References

https://learn.microsoft.com/en-us/azure/devops/pipelines/tasks/reference/manual-validation-v0?view=azure-pipelines