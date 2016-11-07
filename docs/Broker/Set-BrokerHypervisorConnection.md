# Set-BrokerHypervisorConnection

   Sets the properties of a hypervisor connection.

## Syntax
```
Set-BrokerHypervisorConnection [-InputObject] <HypervisorConnection[]> [-PassThru] [-PreferredController <String>] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]

Set-BrokerHypervisorConnection [-Name] <String> [-PassThru] [-PreferredController <String>] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
```

## Detailed Description
   The Set-BrokerHypervisorConnection cmdlet sets the properties on a hypervisor connection.

## Related Commands
  * [Get-BrokerHypervisorConnection](Get-BrokerHypervisorConnection.html)
  * [New-BrokerHypervisorConnection](New-BrokerHypervisorConnection.html)
  * [Remove-BrokerHypervisorConnection](Remove-BrokerHypervisorConnection.html)
## Parameters

| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| InputObject | Specifies the hypervisor connection object to adjust. | true | true (ByValue) |  |
| Name | Specifies the name of the hypervisor connection object to adjust. | true | true (ByPropertyName) |  |
| PassThru | This cmdlet does not generate any output, unless you use the PassThru parameter, in which case it returns the affected record. | false | false | False |
| PreferredController | Supplies the new value of the PreferredController property. | false | false |  |
| LoggingId | Specifies the identifier of the high level operation that this cmdlet call forms a part of. Desktop Studio and Desktop Director typically create High Level Operations. PowerShell scripts can also wrap a series of cmdlet calls in a High Level Operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |

## Input Type
### Citrix.Broker.Admin.SDK.HypervisorConnection
   You can pipe the hypervisor connection to be modified to Set-BrokerHypervisorConnection.
## Return Values
### None or Citrix.Broker.Admin.SDK.HypervisorConnection
   This cmdlet does not generate any output, unless you use the PassThru parameter, in which case it generates a Citrix.Broker.Admin.SDK.HypervisorConnection object.
## Examples

### EXAMPLE 1
```
c:\PS> $hvConn = Get-BrokerHypervisorConnection -PreferredController "oldController" -Name "Xen Server Connection"
c:\PS> Set-BrokerHypervisorConnection -InputObject $hvConn -PreferredController "newController"
```
   Description<br>-----------<br>Updates the preferred controller for a hypervisor connection.
