
# Get-Monitornotificationsnmpserverconfiguration
Gets email server configuration
## Syntax
```
Get-MonitorNotificationSnmpServerConfiguration [-LoggingId <Guid>] [-BearerToken <String>] [-AdminAddress <String>] [<CommonParameters>]
```
## Detailed Description
Returns the existing Snmpserver configurations required to send Snmp alerts.


## Related Commands

* [Set-MonitorNotificationSnmpServerConfiguration](./Set-MonitorNotificationSnmpServerConfiguration/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| LoggingId | Specifies the identifier of the high-level operation this cmdlet call forms a part of. Citrix Studio and Director typically create high-level operations. PowerShell scripts can also wrap a series of cmdlet calls in a high-level operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller the PowerShell snap-in will connect to. You can provide this as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type

### 

## Return Values

### Icollection&lt;Monitornotificationemailserverconfiguration&gt; System.String
Snmp server configuration
## Examples

### Example 1
```
GetMonitorNotificationSnmpServerConfigurationCommand
```
#### Description
Returns the Snmp configuration
