
# Remove-Xdsite
Removes the XenDesktop Site.
## Syntax
```
Remove-XDSite [-AdminAddress <String>] [<CommonParameters>]
```
## Detailed Description
This cmdlet can be executed only when there is one remaining Controller in the Site. It removes the Site by removing the last Controller from the Site.

The person running this command must be a the local administrator on the last Controller in this Site.


## Related Commands

* [New-XDSite](./New-XDSite/)
* [Add-XDController](./Add-XDController/)
* [Remove-XDController](./Remove-XDController/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| AdminAddress | Specifies the address of the Delivery Controller to which the PowerShell module will connect. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |

## Input Type

### None
You cannot pipe input to this cmdlet.
## Return Values

### None

