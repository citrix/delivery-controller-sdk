# Remove-BrokerSessionLinger

   Removes a session linger setting.

## Syntax
```
Remove-BrokerSessionLinger [-InputObject] <SessionLinger[]> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]

Remove-BrokerSessionLinger [-DesktopGroupName] <String> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
```

## Detailed Description
   The Remove-BrokerSessionLinger cmdlet is used to delete an existing session linger setting.

## Related Commands
  * [New-BrokerSessionLinger](New-BrokerSessionLinger.html)
  * [Get-BrokerSessionLinger](Get-BrokerSessionLinger.html)
  * [Set-BrokerSessionLinger](Set-BrokerSessionLinger.html)
## Parameters

| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| InputObject | The session linger setting to be deleted. | true | true (ByValue) |  |
| DesktopGroupName | The name of the desktop group whose session linger setting is to be removed. | true | true (ByPropertyName) |  |
| LoggingId | Specifies the identifier of the high level operation that this cmdlet call forms a part of. Desktop Studio and Desktop Director typically create High Level Operations. PowerShell scripts can also wrap a series of cmdlet calls in a High Level Operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |

## Input Type
### Citrix.Broker.Admin.SDK.SessionLinger
   Session linger settings may be specified through pipeline input.
## Return Values
### None
   
## Examples

### EXAMPLE 1
```
C:\PS> Get-BrokerSessionLinger | Remove-BrokerSessionLinger
```
   Description<br>-----------<br>Deletes every session linger setting for all desktop groups.
