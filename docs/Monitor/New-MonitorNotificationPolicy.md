
# New-Monitornotificationpolicy
Returns a new MonitorNotificationPolicy object
## Syntax
```
New-MonitorNotificationPolicy -Name <String> [-Description <String>] [-Webhook <String>] [-IsSnmpEnabled <Boolean>] [-Enabled <Boolean>] [-LoggingId <Guid>] [-BearerToken <String>] [-AdminAddress <String>] [<CommonParameters>]
```
## Detailed Description
Returns a new policy instance using the specified parameters


## Related Commands

* [Get-MonitorNotificationPolicy](./Get-MonitorNotificationPolicy/)
* [Set-MonitorNotificationPolicy](./Set-MonitorNotificationPolicy/)
* [Remove-MonitorNotificationPolicy](./Remove-MonitorNotificationPolicy/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| Name | Name of policy to create | true | false |  |
| Description | Description of policy to create | false | false |  |
| Webhook | Webhook URL of policy to create | false | false |  |
| IsSnmpEnabled | boolean value representing if SNMP is enabled for new Policy | false | false |  |
| Enabled | Boolean paramter indicating the enabled state of the policy. true – Enabled, false – Disabled | false | false |  |
| LoggingId | Specifies the identifier of the high-level operation this cmdlet call forms a part of. Citrix Studio and Director typically create high-level operations. PowerShell scripts can also wrap a series of cmdlet calls in a high-level operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller the PowerShell snap-in will connect to. You can provide this as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type

### 

## Return Values

### Monitornotificationpolicy
Returns the collection of policy objects created
## Examples

### Example 1
```
New-MonitorNotificationPolicy -Name "Policy1" -Description "Policy Description" -Enabled $true
```
#### Description
Creates session policy and persist the data into database
