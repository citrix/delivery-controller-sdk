
# Get-Xdmonitor
Gets the Monitoring Database attributes of a Site.
## Syntax
```
Get-XDMonitor [-AdminAddress <String>] [<CommonParameters>]
```
## Detailed Description
Gets the Monitoring Database attributes of the Site which has a Controller identified by AdminAddress.


## Related Commands

* [Get-XDSite](./Get-XDSite/)
* [Set-XDMonitor](./Set-XDMonitor/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| AdminAddress | Specifies the address of the Delivery Controller to which the PowerShell module will connect. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |

## Input Type

### None
You cannot pipe input to this cmdlet.
## Return Values

### Citrix.Xendesktoppowershellsdk.Serviceinterfaces.Configuration.Monitor
This includes the name of the Monitoring Database, the database server for the Monitoring Database, the mirror database server for the Monitoring Database and whether Integrated Security is enabled or not for the Monitoring Database.
