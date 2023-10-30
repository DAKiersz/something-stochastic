# Azure Pipelines - Conditional insertion

Conditional (i.e., If) statements use template expression syntax/variables only. Think compile time:

```yaml
${{ if eq( variables['param1'], 'thing1') }}:
	varname: $(variable1)
${{ elseif eq( variables['param2'], 'thing2') }}:
	varname: $(variable2)
${{ else }}:
	varname: $(variable3)
```

## Resources

https://learn.microsoft.com/en-us/azure/devops/pipelines/process/expressions?view=azure-devops#conditional-insertion (Expressions - conditional expression)