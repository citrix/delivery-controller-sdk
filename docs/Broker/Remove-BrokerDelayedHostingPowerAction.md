﻿# Remove-BrokerDelayedHostingPowerAction

   Cancels one or more delayed power actions.

## Syntax
```
Remove-BrokerDelayedHostingPowerAction [-InputObject] <DelayedHostingPowerAction[]> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]

Remove-BrokerDelayedHostingPowerAction [-MachineName] <String> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
```

## Detailed Description
   Removes one or more delayed power actions that have not yet been queued for execution.

## Related Commands
  * [Get-BrokerDelayedHostingPowerAction](Get-BrokerDelayedHostingPowerAction/)
  * [New-BrokerDelayedHostingPowerAction](New-BrokerDelayedHostingPowerAction/)
## Parameters

| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| InputObject | The power action to be cancelled. | true | true (ByValue) |  |
| MachineName | Cancels only actions for machines whose name (of the form domain\machine) matches the specified string. | true | true (ByPropertyName) |  |
| LoggingId | Specifies the identifier of the high level operation that this cmdlet call forms a part of. Desktop Studio and Desktop Director typically create High Level Operations. PowerShell scripts can also wrap a series of cmdlet calls in a High Level Operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |

## Input Type
### Citrix.Broker.Admin.SDK.DelayedHostingPowerAction
   The power action to be cancelled.
## Return Values
### None
   
## Examples

### EXAMPLE 1
```
C:\PS> Remove-BrokerHostingPowerAction -MachineName 'XD_VDA1'
```
   Description<br>-----------<br>Cancels any pending delayed power actions for the machine called XD_VDA1.
