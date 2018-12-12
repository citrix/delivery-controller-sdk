
# Add-Monitornotificationpolicycondition
Add conditions to the existing policy specified and returns the updated policy.
## Syntax
```
Add-MonitorNotificationPolicyCondition -InputObject <MonitorNotificationPolicy> [-AlertThreshold <Int32>] [-AlarmThreshold <Int32>] [-AlertRenotification <TimeSpan>] [-AlarmRenotification <TimeSpan>] [-SearchWindow <TimeSpan>] [-AlertConditionPersistenceInterval <TimeSpan>] [-AlarmConditionPersistenceInterval <TimeSpan>] [-Granularity <TimeSpan>] [-AlertSampleCount <Int32>] [-AlarmSampleCount <Int32>] [-AlertSamplePercent <Int32>] [-AlarmSamplePercent <Int32>] [-LoggingId <Guid>] [-BearerToken <String>] [-AdminAddress <String>] [<CommonParameters>]

Add-MonitorNotificationPolicyCondition -Uid <Int64> -ConditionType <ConditionType> [-AlertThreshold <Int32>] [-AlarmThreshold <Int32>] [-AlertRenotification <TimeSpan>] [-AlarmRenotification <TimeSpan>] [-SearchWindow <TimeSpan>] [-AlertConditionPersistenceInterval <TimeSpan>] [-AlarmConditionPersistenceInterval <TimeSpan>] [-Granularity <TimeSpan>] [-AlertSampleCount <Int32>] [-AlarmSampleCount <Int32>] [-AlertSamplePercent <Int32>] [-AlarmSamplePercent <Int32>] [-LoggingId <Guid>] [-BearerToken <String>] [-AdminAddress <String>] [<CommonParameters>]
```
## Detailed Description
Add conditions to the existing policy specified and returns the updated policy.


## Related Commands

* [Get-MonitorNotificationPolicy](./Get-MonitorNotificationPolicy/)
* [Set-MonitorNotificationPolicy](./Set-MonitorNotificationPolicy/)
* [Remove-MonitorNotificationPolicy](./Remove-MonitorNotificationPolicy/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| InputObject | Specifies the policy object to which the conditions to be added | true | true (ByValue) |  |
| Uid | Specifies the unique identifier of the policy to which the conditions to be added | true | false |  |
| ConditionType | Type of the condition using a text string converted to an enum value Possible values are SessionsConcurrentCount SessionsPeakconnectedCount SessionsPeakDisconnectedCount AverageLogonDuration RDSLoadEvaluator ConnectionFailuresRate ConnectionFailuresCount FailedServerMachineCount FailedDesktopMachineCount LogonDuration IcaRoundtripTime IcaRoundtripTimeAverage IcaRoundtripTimeSessionCount IcaRoundtripTimeSessionPercent MemoryUsage CpuUsage | true | false |  |
| AlertThreshold | Threshold value at which the warning notification will be triggered | false | false |  |
| AlarmThreshold | Threshold value at which the critical notification will be triggered | false | false |  |
| AlertRenotification | Duration after which the warning notification will be re-triggered | false | false |  |
| AlarmRenotification | Duration after which the critical notification will be re-triggered | false | false |  |
| SearchWindow | The amount of time the condition query will look back for the matching record when it examines the data. | false | false |  |
| AlertConditionPersistenceInterval | The amount of time the condition query will look back to check if the alert condition was persisted. | false | false |  |
| AlarmConditionPersistenceInterval | The amount of time the condition query will look back to check if the alarm condition was persisted. | false | false |  |
| Granularity | Defines the granularity of the rate in seconds. This value is applicable for ‘ConnectionFailuresRate’ condition. | false | false |  |
| AlertSampleCount | Defines the count of instances to measure before raising the warning notification. This value is applicable for ICA RTT (Session Count) condition. | false | false |  |
| AlarmSampleCount | Defines the count of instances to measure before raising the critical notification. This value is applicable for ICA RTT (Session Count) condition. | false | false |  |
| AlertSamplePercent | Defines the percentage of instances to measure before raising the warning notification. This value is applicable for ICA RTT (Session Percent) condition. | false | false |  |
| AlarmSamplePercent | Defines the percentage of instances to measure before raising the critical notification. This value is applicable for ICA RTT (Session Percent) condition. | false | false |  |
| LoggingId | Specifies the identifier of the high-level operation this cmdlet call forms a part of. Citrix Studio and Director typically create high-level operations. PowerShell scripts can also wrap a series of cmdlet calls in a high-level operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller the PowerShell snap-in will connect to. You can provide this as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type

### 

## Return Values

### Monitornotificationpolicy
Returns the updated policy object
## Examples

### Example 1
```
$timeSpan = New-TimeSpan -Seconds 30

          $alertThreshold = 10

          $alarmThreshold = 20

          Add-MonitorNotificationPolicyCondition -Uid 100 -ConditionType SessionsConcurrentCount -AlertThreshold $alertThreshold -AlarmThreshold $alarmThreshold  -AlertRenotification $timeSpan -AlarmRenotification $timeSpan
```
#### Description
Add SessionsConcurrentCount condition to the policy matching the id 100
