# Get-MonitorNotificationPolicy

   Returns a list of MonitorNotificationPolicy objects matching the specified parameters

## Syntax
```
Get-MonitorNotificationPolicy [-Uid <Int64>] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]

Get-MonitorNotificationPolicy -Name <String> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
```

## Detailed Description
   Returns a list of MonitorNotificationPolicy objects matching the specified parameters

## Related Commands
  * [New-MonitorNotificationPolicy](New-MonitorNotificationPolicy/)
  * [Remove-MonitorNotificationPolicy](Remove-MonitorNotificationPolicy/)
  * [Set-MonitorNotificationPolicy](Set-MonitorNotificationPolicy/)
## Parameters

| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| Name | Returns all of the policies contains the specified name. | true | false |  |
| Uid | Returns the policy with the specified id. | false | false |  |
| LoggingId | Specifies the identifier of the high-level operation this cmdlet call forms a part of. Citrix Studio and Director typically create high-level operations. PowerShell scripts can also wrap a series of cmdlet calls in a high-level operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller the PowerShell snap-in will connect to. You can provide this as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type
### 
   
## Return Values
### System.Collections.Generic.ICollection`1[[Citrix.Monitor.Sdk.PowerShell.MonitorNotificationPolicy, Citrix.Monitor.PowerShellSnapIn, Version=7.7.0.95, Culture=neutral, PublicKeyToken=e6a2b8abcb991548]]
   Returns a collection of policies.
## Examples

### EXAMPLE 1
```
Get-MonitorNotificationPolicy -Id 1
```
   Description<br>-----------<br>Returns the policy object having the Id equals to 1
### EXAMPLE 2
```
Get-MonitorNotificationPolicy -Name 'Server OS Policy'
```
   Description<br>-----------<br>Returns the policy object having the name contains 'Server OS Policy'
