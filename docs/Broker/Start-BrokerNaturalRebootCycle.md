# Start-BrokerNaturalRebootCycle

   Reboots all machines from the specified catalog when they are not in use.

## Syntax
```
Start-BrokerNaturalRebootCycle [-InputObject] <Catalog[]> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
```

## Detailed Description
   Creating a natural reboot cycle for a catalog ensures that all machines in the catalog are running the most recent image for the catalog.

The machines are rebooted in a non-disruptive manner, allowing machines that are in use to continue working and be restarted only after they become idle.

## Related Commands
  * [Start-BrokerRebootCycle](Start-BrokerRebootCycle.html)
  * [Start-BrokerDesktopGroupRebootCycle](Start-BrokerDesktopGroupRebootCycle.html)
  * [Start-BrokerNaturalDesktopGroupRebootCycle](Start-BrokerNaturalDesktopGroupRebootCycle.html)
## Parameters

| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| InputObject | Reboots all machines from this input catalog. The catalogs can be specified using UID values, name values (including wildcards) or catalog objects. | true | true (ByValue) |  |
| LoggingId | Specifies the identifier of the high level operation that this cmdlet call forms a part of. Desktop Studio and Desktop Director typically create High Level Operations. PowerShell scripts can also wrap a series of cmdlet calls in a High Level Operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |

## Input Type
### Citrix.Broker.Admin.SDK.Catalog
   Catalogs may be specified through pipeline input. The catalogs can be specified using UID values, name values (including wildcards) or catalog objects
## Return Values
### None
   ## Notes
   Natural reboot cycles do not apply to non-power managed and multi session catalogs
## Examples

### EXAMPLE 1
```
$c = Get-BrokerCatalog -Uid 1
          Start-BrokerNaturalRebootCycle -InputObject $c
```
   Description<br>-----------<br>The above code applies a natural reboot cycle on catalog with Id 1
