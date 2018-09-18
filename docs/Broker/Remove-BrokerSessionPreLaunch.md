# Remove-BrokerSessionPreLaunch

   Removes a session pre-launch setting.

## Syntax
```
Remove-BrokerSessionPreLaunch [-InputObject] <SessionPreLaunch[]> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]

Remove-BrokerSessionPreLaunch [-DesktopGroupName] <String> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
```

## Detailed Description
   The Remove-BrokerSessionPreLaunch cmdlet is used to delete an existing session pre-launch setting.

## Related Commands
  * [New-BrokerSessionPreLaunch](New-BrokerSessionPreLaunch/)
  * [Get-BrokerSessionPreLaunch](Get-BrokerSessionPreLaunch/)
  * [Set-BrokerSessionPreLaunch](Set-BrokerSessionPreLaunch/)
## Parameters

| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| InputObject | The session pre-launch setting to be deleted. | true | true (ByValue) |  |
| DesktopGroupName | The name of the desktop group whose session pre-launch setting is to be removed. | true | true (ByPropertyName) |  |
| LoggingId | Specifies the identifier of the high level operation that this cmdlet call forms a part of. Desktop Studio and Desktop Director typically create High Level Operations. PowerShell scripts can also wrap a series of cmdlet calls in a High Level Operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |

## Input Type
### Citrix.Broker.Admin.SDK.SessionPreLaunch
   Session pre-launch settings may be specified through pipeline input.
## Return Values
### None
   
## Examples

### EXAMPLE 1
```
C:\PS> Get-BrokerSessionPreLaunch | Remove-BrokerSessionPreLaunch
```
   Description<br>-----------<br>Deletes every session pre-launch setting for all desktop groups.
