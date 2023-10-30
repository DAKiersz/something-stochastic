# Azure Pipelines - Useful Builtin Vars

For YAML Pipelines:

* `$(Build.BuildNumber)` - The unique pipeline run number, equivalent to `Release.ReleaseName` in release pipelines.
* `$(System.JobAttempt)` - Job attempt number, equivalent to `Release.AttemptNumber` in release pipelines.