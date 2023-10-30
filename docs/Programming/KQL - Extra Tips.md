# KQL - Extra Tips

## `countof`

`countof` counts occurences of a substring in a string. The syntax is:

`countof(text, search [, kind])`

## Time Queries

A simple `where` filter for time frame:

```sql
where TimeGenerated between(ago(365d) .. now())
where TimeGenerated between (datatime(2020-07-01) .. datetime(2020-07-30, 09:00))
```

Using an `iff` statement which creates a variable `dateTimeToValidate` based on current time (`now()`)

```sql
let dateTimeToValidate = iff((dateime_part('minute', now()) < 30), now(-1h), now());
```

## Parse JSON 

We can use  `parse_json` to parse details of a JSON result. In this instance, its the `ADFPipelineRun` column from Azure Data Factory

```sql
ADFPipelineRun
	| extend TableName=tostring(parse_json(Parameters).tableName), PipelineStart=Start
```

## Misc.

* The "dynamic data type" is  effectively a JSON Array. AzureDiagnostics table in Log Analytics can use this to this should it reach the limit of 500 columns.
