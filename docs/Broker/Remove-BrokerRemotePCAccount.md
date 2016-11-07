# Remove-BrokerRemotePCAccount

   Delete RemotePCAccounts from the system.

## Syntax
```
Remove-BrokerRemotePCAccount [-InputObject] <RemotePCAccount[]> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
```

## Detailed Description
   Delete RemotePCAccounts from the site.

## Related Commands
  * [Get-BrokerRemotePCAccount](Get-BrokerRemotePCAccount.html)
  * [New-BrokerRemotePCAccount](New-BrokerRemotePCAccount.html)
  * [Set-BrokerRemotePCAccount](Set-BrokerRemotePCAccount.html)
## Parameters

| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| InputObject | Specifies the RemotePCAccounts to delete. | true | true (ByValue) | null |
| LoggingId | Specifies the identifier of the high level operation that this cmdlet call forms a part of. Desktop Studio and Desktop Director typically create High Level Operations. PowerShell scripts can also wrap a series of cmdlet calls in a High Level Operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |

## Input Type
### Citrix.Broker.Admin.SDK.RemotePCAccount
   You can pipe the RemotePCAccounts to be deleted into this cmdlet.
## Return Values
### None
   
## Examples

### EXAMPLE 1
```
C:\PS> Remove-BrokerRemotePCAccount 42
```
   Description<br>-----------<br>Delete RemotePCAccount 42.
### EXAMPLE 2
```
C:\PS> Get-BrokerRemotePCAccount -OU 'any' | Remove-BrokerRemotePCAccount
```
   Description<br>-----------<br>Delete the 'any' OU RemotePCAccount.
### EXAMPLE 3
```
C:\PS> Get-BrokerRemotePCAccount | Remove-BrokerRemotePCAccount
```
   Description<br>-----------<br>Delete all RemotePCAccounts.
