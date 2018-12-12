
# Remove-Monitornotificationpolicyconditions
Remove conditions from the existing policy specified and returns the updated policy.
## Syntax
```
Remove-MonitorNotificationPolicyConditions -InputObject <MonitorNotificationPolicy> -Conditions <ConditionType[]> [-LoggingId <Guid>] [-BearerToken <String>] [-AdminAddress <String>] [<CommonParameters>]

Remove-MonitorNotificationPolicyConditions -Uid <Int64> -Conditions <ConditionType[]> [-LoggingId <Guid>] [-BearerToken <String>] [-AdminAddress <String>] [<CommonParameters>]
```
## Detailed Description
Remove conditions from the existing policy specified and returns the updated policy.


## Related Commands

* [Get-MonitorNotificationPolicy](./Get-MonitorNotificationPolicy/)
* [Set-MonitorNotificationPolicy](./Set-MonitorNotificationPolicy/)
* [Remove-MonitorNotificationPolicy](./Remove-MonitorNotificationPolicy/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| InputObject | Specifies the policy object from which the conditions to be removed. | true | true (ByValue) |  |
| Conditions | Collection of condition types to be removed | true | false |  |
| Uid | Specifies the unique identifier of the policy from which the conditions to be removed. | true | false |  |
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
Remove-MonitorNotificationPolicyConditions -Uid 100 -Conditions SessionsPeakconnectedCount
```
#### Description
Removes the condition SessionPeakconnectedCount from policy matching id 100
