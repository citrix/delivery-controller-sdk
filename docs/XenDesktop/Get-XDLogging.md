
# Get-Xdlogging
Gets the Configuration Logging Database attributes of a Site.
## Syntax
```
Get-XDLogging [-AdminAddress <String>] [<CommonParameters>]
```
## Detailed Description
Gets the Configuration Logging Database attributes of the Site which has a Controller identified by AdminAddress.


## Related Commands

* [Get-XDSite](./Get-XDSite/)
* [Set-XDLogging](./Set-XDLogging/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| AdminAddress | Specifies the address of the Delivery Controller to which the PowerShell module will connect. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |

## Input Type

### None
You cannot pipe input to this cmdlet.
## Return Values

### Citrix.Xendesktoppowershellsdk.Serviceinterfaces.Configuration.Logging
This includes whether Logging is enabled or not, whether configuration operations may proceed or not, even if the Configuration Logging Database is not available, the language used for Configuration Logging entries, the name of the Configuration Logging Database, the database server for the Configuration Logging Database, the mirror database server for the Configuration Logging Database and whether Integrated Security is enabled or not for the Configuration Logging Database.
