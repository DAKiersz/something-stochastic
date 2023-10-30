# KQL - Basic MS Reference

## Queries

A query is a data source (usually a table name) followed by one or more pipes and **tabular** operator.

## count

*The [InsightsMetrics](https://learn.microsoft.com/en-us/azure/azure-monitor/reference/tables/insightsmetrics) table contains performance data that's collected by insights such as **Azure Monitor for VMs** and **Azure Monitor for containers***

```KQL
InsightsMetrics | count
```

Results from `InsightsMetrics` table are returns and sent to the `count` operator.

## where

*The [AzureActivity](https://learn.microsoft.com/en-us/azure/azure-monitor/reference/tables/azureactivity) table has entries from the **Azure activity** log, which provides insight into subscription-level or management group-level **events** occuring in Azure.*

```KQL
AzureActivity
| where TimeGenerated > datetime(10-01-2020) and TimeGenerated < datetime(10-07-2020)
| where Level == 'Critical'
```

Similar to `WHERE` in SQL

## project

Use [project](https://learn.microsoft.com/en-us/azure/data-explorer/kusto/query/projectoperator) to include only the columns you want.

```KQL
AzureActivity
| where TimeGenerated > datetime(10-01-2020) and TimeGenerated < datetime(10-07-2020)
| where Level == 'Critical'
| project TimeGenerated, Level, OperationNameValue, ResourceGroup, _ResourceId
```

In here, we have `TimeGenerated`, Level etc. columns. This acts like `SELECT` in SQL

## take

[NetworkMonitoring](https://learn.microsoft.com/en-us/azure/azure-monitor/reference/tables/networkmonitoring) contains monitoring data for Azure **virtual networks**.

Take operator looks at 10 random sample rows in that table.

```KQL
NetworkMonitoring
| take 10
| project TimeGenerated, Computer, SourceNetwork, DestinationNetwork, HighLatency, LowLatency
```

## sort, top

Instead of random - return latest five records (by time)

```KQL
NetworkMonitoring
| sort by TimeGenerated desc
| take 5
| project TimeGenerated, Computer, SourceNetwork, DestinationNetwork, HighLatency, LowLatency
```

alternatively:

```KQL
NetworkMonitoring
| top 5 by TimeGenerated desc
| project TimeGenerated, Computer, SourceNetwork, DestinationNetwork, HighLatency, LowLatency
```

sort and take are **not** random.

(Similar to  `ORDER BY`)

## extend

*The [Perf](https://learn.microsoft.com/en-us/azure/azure-monitor/reference/tables/perf) table has performance data that's collected from **virtual machines** that run the Log Analytics agent.*

The [extend](https://learn.microsoft.com/en-us/azure/data-explorer/kusto/query/projectoperator) operator is similar to [project](https://learn.microsoft.com/en-us/azure/data-explorer/kusto/query/projectoperator), but it **adds** to the set of columns instead of **replacing** them. You can use **both** operators to create a new column based on a computation on each row.

``` KQL
Perf
| where ObjectName == "LogicalDisk" and CounterName == "Free Megabytes"
| project TimeGenerated, Computer, FreeMegabytes = CounterValue
| extend FreeGigabytes = FreeMegabytes / 1000
```

##  summarize

*The [SecurityEvent](https://learn.microsoft.com/en-us/azure/azure-monitor/reference/tables/securityevent) table contains security events like **logons** and **processes** that started on monitored computers. You can count how many events of each level occurred on each computer.*

The [summarize](https://learn.microsoft.com/en-us/azure/data-explorer/kusto/query/summarizeoperator) operator groups together rows that have the same values in the `by` clause.

Then, it uses an aggregation function like `count` to combine each group in a single row. A range of [aggregation functions](https://learn.microsoft.com/en-us/azure/data-explorer/kusto/query/aggregation-functions) are available.

```KQL
SecurityEvent
| summarize count() by Computer, Level
```

*In this example, a row is produced for each **computer** and **level** combination. A column contains the count of events.*

Works like `GROUP BY` 

## Summarise by scalars:

*You can aggregate by scalar values like **numbers** and **time** values, but you should use the [bin()](https://learn.microsoft.com/en-us/azure/data-explorer/kusto/query/binfunction) function to group rows into distinct **sets** of data.*

The following query shows the hourly average processor utilization for multiple computers:

```KQL
InsightsMetrics
| where Computer startswith "DC"
| where Namespace  == "Processor" and Name == "UtilizationPercentage"
| summarize avg(Val) by Computer, bin(TimeGenerated, 1h)
```

You can also render multiple serioes.

```KQL
render timechart
```

## Join data from two tables

The `join` operator to combine rows from multiple tables in a single result set.

Each table must have a column that has a matching value

```KQL 
VMComputer
| distinct Computer, PhysicalMemoryMB
| join kind=inner (
    InsightsMetrics
    | where Namespace == "Memory" and Name == "AvailableMB"
    | project TimeGenerated, Computer, AvailableMemoryMB = Val
) on Computer
| project TimeGenerated, Computer, PercentMemory = AvailableMemoryMB / PhysicalMemoryMB * 100
```

The `distinct` keyword is similar to  `SELECT DISTINCT` statement, which is used to return only distinct values.

## let

Setting **to** a variable.

*Use [let](https://learn.microsoft.com/en-us/azure/data-explorer/kusto/query/letstatement) to make queries easier to read and manage. You can use this operator to assign the results of a query to a variable that you can use later*

```KQL
let PhysicalComputer = VMComputer
    | distinct Computer, PhysicalMemoryMB;
let AvailableMemory = InsightsMetrics
    | where Namespace == "Memory" and Name == "AvailableMB"
    | project TimeGenerated, Computer, AvailableMemoryMB = Val;
PhysicalComputer
| join kind=inner (AvailableMemory) on Computer
| project TimeGenerated, Computer, PercentMemory = AvailableMemoryMB / PhysicalMemoryMB * 100
```

## References

* https://learn.microsoft.com/en-us/azure/data-explorer/kusto/query/ (overview)
* https://learn.microsoft.com/en-us/azure/data-explorer/kql-quick-reference (quick reference)
* https://learn.microsoft.com/en-us/azure/data-explorer/kusto/query/tutorials/learn-common-operators?pivots=azuremonitor (tutorial - common operators)
