
# Get-Xdsite
Gets the attributes of a Site.
## Syntax
```
Get-XDSite [-AdminAddress <String>] [<CommonParameters>]
```
## Detailed Description
Gets the attributes of the Site which has a Controller identified by AdminAddress.


## Related Commands

* [New-XDSite](./New-XDSite/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| AdminAddress | Specifies the address of the Delivery Controller to which the PowerShell module will connect. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |

## Input Type

### None
You cannot pipe input into this cmdlet.
## Return Values

### Citrix.Xendesktoppowershellsdk.Serviceinterfaces.Configuration.Site
This includes the name of the Site, the Controllers in Site, the Databases supporting the Site,  the licensing configuration of the Site and the default Icon for the Site.
## Examples

### Example 1
```
C:\PS> Get-XDSite -AdminAddress MySiteController
```
#### Description
Gets the attributes of the Site which has a Controller identified by MySiteController.
