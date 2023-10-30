# Azure Pipelines - Bicep Validation with a Matrix Strategy

A sample template for validating multiple Bicep deployment files (components in this case) against different environments using a **matrix** strategy. This can be put in a stage on its own validating all deployments before going into dev, staging etc.

```yaml
 jobs: 
  - job: 
	displayName: "Validate Deployment: "
	strategy:
	  matrix: 
		'Development Component 1':
		  env: 'dev'
		  component: 'component1'
		'Development Component 2':
		  env: 'dev'
		  component: 'component2'
		'Staging Component 1':
		  env: 'staging'
		  component: 'component1'
		'Staging Component 2':
		  env: 'staging'
		  component: 'component2'
		'Production Component 1':
		  env: 'prod'
		  component: 'component1'
		'Production Component 2':
		  env: 'prod'
		  component: 'component2'
	pool: ubuntu-latest
	variables:
		mode: 'Validation'
		location: 'westeurope'
	steps:
	  - task: AzureResourceManagerTemplateDeployment@3
		displayName: "Task - Validate $(component) deployment against $(env)"
		inputs:
		  deploymentScope: 'Subscription'
		  azureResourceManagerConnection: xxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
		  subscriptionId: xxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
		  action: 'Create Or Update Resources'
		  location: location
		  templateLocation: 'Linked artifact'
		  csmFile: main.bicep
		  csmParametersFile: parameters.json'
		  deploymentMode: $(mode)
		  deploymentName: $(env)-$(component)-validation-$(Build.BuildId)
```

Note that this strategy will produce 4 jobs at a **runtime** of the pipeline. That means using `${{}}` expression (a.k.a. template expression variables) will not work inside this job, as these expressions are evaluated at **compile time** (of the YAML pipeline itself) instead!

You can however use macro declarations like `$(env)` to call attributes of each matrix combination or call from variables. 

The pipeline job displayname will be will return the title of each matrix instance appended to  `displayName: "Validate Deployment: "`  e.g.,  `Validate Deployment: Development Component 1`

## References

https://learn.microsoft.com/en-us/azure/devops/pipelines/tasks/reference/azure-resource-manager-template-deployment-v3?view=azure-pipelines (Microsoft documentation - Azure Pipeline task for deploying ARM/Bicep templates)

https://learn.microsoft.com/en-us/azure/devops/pipelines/yaml-schema/jobs-job-strategy?view=azure-pipelines (Microsoft documentation  - `strategy` keyword definition)

https://learn.microsoft.com/en-us/azure/devops/pipelines/process/expressions?view=azure-devops (Expressions)

https://learn.microsoft.com/en-us/azure/devops/pipelines/process/runtime-parameters?view=azure-devops&tabs=script (Runtime parameters)

https://learn.microsoft.com/en-us/azure/devops/pipelines/process/variables?view=azure-devops&tabs=yaml%2Cbatch#understand-variable-syntax (Variable syntax)

https://mattvsts.github.io/2020/01/07/create-a-build-matrix-with-azure-pipelines/ (An excellent blog post about using matrix jobs in more detail)

