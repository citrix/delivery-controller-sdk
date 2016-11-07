# Remove-BrokerHostingPowerAction

   Cancel one or more pending power actions.

## Syntax
```
Remove-BrokerHostingPowerAction [-InputObject] <HostingPowerAction[]> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]

Remove-BrokerHostingPowerAction [-MachineName] <String> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
```

## Detailed Description
   Causes one or more of the pending power actions in the queue to be marked as cancelled. The affected power actions are not sent to the hypervisor for processing, and take no further part in the queuing activity.

Power actions cannot be cancelled once they have started to be processed by the hypervisor.

## Related Commands
  * [Get-BrokerHostingPowerAction](Get-BrokerHostingPowerAction.html)
  * [New-BrokerHostingPowerAction](New-BrokerHostingPowerAction.html)
  * [Set-BrokerHostingPowerAction](Set-BrokerHostingPowerAction.html)
## Parameters

| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| InputObject | The power action to be cancelled. | true | true (ByValue) |  |
| MachineName | Cancels only actions for machines whose name (of the form domain\machine) matches the specified string. | true | true (ByPropertyName) |  |
| LoggingId | Specifies the identifier of the high level operation that this cmdlet call forms a part of. Desktop Studio and Desktop Director typically create High Level Operations. PowerShell scripts can also wrap a series of cmdlet calls in a High Level Operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |

## Input Type
### Citrix.Broker.Admin.SDK.HostingPowerAction
   The power action to be cancelled.
## Return Values
### None
   
## Examples

### EXAMPLE 1
```
C:\PS> Remove-BrokerHostingPowerAction -MachineName 'XD_VDA1'
```
   Description<br>-----------<br>Cancels any pending power actions for the machine called 'XD_VDA1'.
### EXAMPLE 2
```
C:\PS> Get-BrokerHostingPowerAction -Filter { State -eq "Pending" -and RequestTime -gt "-00:05" } | Remove-BrokerHostingPowerAction
```
   Description<br>-----------<br>Cancels any pending power actions requested in the last five minutes.
