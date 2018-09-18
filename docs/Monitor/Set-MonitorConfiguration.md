# Set-MonitorConfiguration

   Sets configuration settings that are used by the Monitor Service.

## Syntax
```
Set-MonitorConfiguration [-GroomSessionsRetentionDays <Int32>] [-GroomFailuresRetentionDays <Int32>] [-GroomLoadIndexesRetentionDays <Int32>] [-GroomDeletedRetentionDays <Int32>] [-GroomSummariesRetentionDays <Int32>] [-GroomMachineHotfixLogRetentionDays <Int32>] [-GroomMinuteRetentionDays <Int32>] [-GroomHourlyRetentionDays <Int32>] [-DataCollectionEnabled <Boolean>] [-FullPollStartHour <Int32>] [-ResolutionPollTimeHours <Int32>] [-SyncPollTimeHours <Int32>] [-DetailedSqlOutputEnabled <Boolean>] [-MonitorQueryTimeoutSeconds <Int32>] [-CollectHotfixDataEnabled <Boolean>] [-GroomApplicationInstanceRetentionDays <Int32>] [-GroomNotificationLogRetentionDays <Int32>] [-GroomResourceUsageRawDataRetentionDays <Int32>] [-GroomResourceUsageMinuteDataRetentionDays <Int32>] [-GroomResourceUsageHourDataRetentionDays <Int32>] [-GroomResourceUsageDayDataRetentionDays <Int32>] [-GroomProcessUsageRawDataRetentionDays <Int32>] [-GroomProcessUsageMinuteDataRetentionDays <Int32>] [-GroomProcessUsageHourDataRetentionDays <Int32>] [-GroomProcessUsageDayDataRetentionDays <Int32>] [-GroomSessionMetricsDataRetentionDays <Int32>] [-EnableDayLevelGranularityProcessUtilization <Boolean>] [-EnableHourLevelGranularityProcessUtilization <Boolean>] [-EnableMinLevelGranularityProcessUtilization <Boolean>] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
```

## Detailed Description
   Sets the configuration settings used by the Monitor Service. Use these settings to modify the behavior of the service.

A database connection need not be configured for this command to be used.

## Related Commands
  * [Get-MonitorConfiguration](Get-MonitorConfiguration/)
## Parameters

| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| GroomSessionsRetentionDays | Determines how many days to keep Session and Connection records after the Session is terminated. | false | false | 7 for non-platinum, 90 for platinum. |
| GroomFailuresRetentionDays | Determines how many days to keep MachineFailureLog and ConnectionFailureLog records after these are created. | false | false | 7 for non-platinum, 90 for platinum. |
| GroomLoadIndexesRetentionDays | Determines how many days to keep LoadIndex records after these are created. | false | false | 7 for non-platinum, 90 for platinum. |
| GroomDeletedRetentionDays | Determines how many days to keep Machine, Catalog, DesktopGroup and Hypervisor entities around that have a LifecycleState of ‘Deleted’.  This also deletes any related Session, Connection, Summary, Failure or LoadIndex records. | false | false | 7 for non-platinum, 90 for platinum. |
| GroomSummariesRetentionDays | Determines how many days to keep DesktopGroupSummary, FailureLogSummary and LoadIndexSummary records at the daily granularity. | false | false | 7 for non-platinum, 90 for platinum. |
| GroomMachineHotfixLogRetentionDays | Determines how many days to keep Machine-Hotfix history records at the daily granularity. | false | false | 90 |
| GroomMinuteRetentionDays | Determines how many days to keep minute data. | false | false | 3 |
| GroomHourlyRetentionDays | Determines how many days to keep hourly data. | false | false | 7 for non-platinum, 32 for platinum. |
| DataCollectionEnabled | Starts / stops data collection.  Stopping data collection turns off polling, and does not persist operational event data to the database. | false | false | True |
| FullPollStartHour | Hour of day when Full Poll should begin. | false | false |  |
| ResolutionPollTimeHours | Start time for the Resolution Poll worker. | false | false |  |
| SyncPollTimeHours | Start time for Sync Poll worker. | false | false |  |
| DetailedSqlOutputEnabled | Determines if the SqlLog should be enabled to send SQL statements to the CDF Trace | false | false | False |
| MonitorQueryTimeoutSeconds | Determines the maximum time Monitoring Service will wait for the database query execution | false | false | 300 |
| CollectHotfixDataEnabled | This setting determines if the hotfix inventory data should be collected and stored in the database or if it should be thrown away. | false | false |  |
| GroomApplicationInstanceRetentionDays | Determines how many days to keep the history of application instances. | false | false | 0 for non-platinum, 90 for platinum. |
| GroomNotificationLogRetentionDays | FIXME | false | false |  |
| GroomResourceUsageRawDataRetentionDays | Determines how many days to keep Resource Utilization data. | false | false | 1 for non-platinum and platinum. |
| GroomResourceUsageMinuteDataRetentionDays | Determines how many days to keep Resource Utilization summary minute data. | false | false | 7 for non-platinum and platinum. |
| GroomResourceUsageHourDataRetentionDays | Determines how many days to keep Resource Utilization summary hour data. | false | false | 7 for non-platinum and 30 for platinum. |
| GroomResourceUsageDayDataRetentionDays | Determines how many days to keep Resource Utilization summary day data. | false | false | 7 for non-platinum and 90 for platinum. |
| GroomProcessUsageRawDataRetentionDays | Determines how many days to keep Process Utilization data. | false | false | 1 for non-platinum and platinum. |
| GroomProcessUsageMinuteDataRetentionDays | Determines how many days to keep Process Utilization summary minute data. | false | false | 3 for non-platinum and platinum. |
| GroomProcessUsageHourDataRetentionDays | Determines how many days to keep Process Utilization summary hour data. | false | false | 7 for non-platinum and platinum. |
| GroomProcessUsageDayDataRetentionDays | Determines how many days to keep Process Utilization summary day data. | false | false | 7 for non-platinum and 30 for platinum. |
| GroomSessionMetricsDataRetentionDays | Determines how many days to keep SessionMetrics data. | false | false | 7 for non-platinum and platinum. |
| EnableDayLevelGranularityProcessUtilization | This setting is used to determine to enable or disable Day Level granularity for Process Data. | false | false |  |
| EnableHourLevelGranularityProcessUtilization | This setting is used to determine to enable or disable Hour Level granularity for Process Data. | false | false |  |
| EnableMinLevelGranularityProcessUtilization | This setting is used to determine to enable or disable Minute Level granularity for Process Data. | false | false |  |
| LoggingId | Specifies the identifier of the high-level operation this cmdlet call forms a part of. Citrix Studio and Director typically create high-level operations. PowerShell scripts can also wrap a series of cmdlet calls in a high-level operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller the PowerShell snap-in will connect to. You can provide this as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type
### 
   
## Return Values
### 
   
## Examples

### EXAMPLE 1
```
C:\PS>Set-MonitorConfiguration -GroomSessionsRetentionDays 5 -GroomFailuresRetentionDays 4 ...
```
   Description<br>-----------<br>Updates the settings in the site database with the newly specified values.
