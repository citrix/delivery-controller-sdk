# Remove-BrokerMachineConfiguration

   Deletes a machine configuration from the site or removes the association from a desktop group.

## Syntax
```
Remove-BrokerMachineConfiguration [-InputObject] <MachineConfiguration[]> [-Application <Application>] [-DesktopGroup <DesktopGroup>] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]

Remove-BrokerMachineConfiguration [-Name] <String> [-Application <Application>] [-DesktopGroup <DesktopGroup>] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
```

## Detailed Description
   This cmdlet has three functions:
o Break associations between desktop groups and machine configurations.
o Break associations between applications and machine configurations.
o Remove machine configurations from the system.

If no desktop group or application is specified, then the Remove-MachineConfiguration cmdlet removes the machine configuration from the site.

If a desktop group is specified, then the Remove-MachineConfiguration cmdlet removes the association between the machine configuration and that desktop group. In this case, the machine configuration is not removed from the site.

If an application is specified, then the Remove-MachineConfiguration cmdlet removes the association between the machine configuration and that application. Again, in this case, the machine configuration is not removed from the site.

## Related Commands
  * [New-BrokerMachineConfiguration](New-BrokerMachineConfiguration.html)
  * [Get-BrokerMachineConfiguration](Get-BrokerMachineConfiguration.html)
  * [Set-BrokerMachineConfiguration](Set-BrokerMachineConfiguration.html)
  * [Rename-BrokerMachineConfiguration](Rename-BrokerMachineConfiguration.html)
  * [Add-BrokerMachineConfiguration](Add-BrokerMachineConfiguration.html)
## Parameters

| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| InputObject | Machine configuration to remove. | true | true (ByValue) | None |
| Name | Name of machine configuration for which the remove operation applies. | true | true (ByPropertyName) | None |
| Application | The application from which this machine configuration is to be removed. | false | true (ByValue) | None |
| DesktopGroup | The desktop group from which this machine configuration is to be removed. | false | true (ByValue) | None |
| LoggingId | Specifies the identifier of the high level operation that this cmdlet call forms a part of. Desktop Studio and Desktop Director typically create High Level Operations. PowerShell scripts can also wrap a series of cmdlet calls in a High Level Operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |

## Input Type
### Citrix.Broker.Admin.SDK.MachineConfiguration
   Machine configuration to remove
## Return Values
### None
   ## Notes
   A machine configuration can only be removed if it is not currently applied to a desktop group.
## Examples

### EXAMPLE 1
```
Remove-BrokerMachineConfiguration -Name UPM\Finance
```
   Description<br>-----------<br>Removes the machine configuration named "UPM\Finance".
### EXAMPLE 2
```
Remove-BrokerMachineConfiguration -Name Receiver\HumanResources -DesktopGroup SharedWorkers
```
   Description<br>-----------<br>Removes the association of the machine configuration named "Receiver\HumanResources" from the "SharedWorkers" desktop group.
