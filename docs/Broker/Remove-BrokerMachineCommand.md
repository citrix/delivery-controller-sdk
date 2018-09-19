# Remove-BrokerMachineCommand

   Cancel a pending command queued for delivery to a desktop.

## Syntax
```
Remove-BrokerMachineCommand [-InputObject] <MachineCommand[]> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
```

## Detailed Description
   Sets the state of a pending command queued for delivery to a desktop to Canceled. The command is not removed from the system.

## Related Commands
  * [Get-BrokerMachineCommand](Get-BrokerMachineCommand/)
  * [New-BrokerMachineCommand](New-BrokerMachineCommand/)
## Parameters

| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| InputObject | Commands to cancel. | true | true (ByValue) |  |
| LoggingId | Specifies the identifier of the high level operation that this cmdlet call forms a part of. Desktop Studio and Desktop Director typically create High Level Operations. PowerShell scripts can also wrap a series of cmdlet calls in a High Level Operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |

## Input Type
### Citrix.Broker.Admin.SDK.MachineCommand
   Commands to cancel.
## Return Values
### None
   
## Examples

### EXAMPLE 1
```
Get-BrokerMachineCommand | Remove-BrokerMachineCommand
```
   Description<br>-----------<br>Cancel all pending commands.
### EXAMPLE 2
```
Get-BrokerMachineCommand -Category "UPM" | Remove-BrokerMachineCommand
```
   Description<br>-----------<br>Cancel all pending commands that have the category "UPM".
