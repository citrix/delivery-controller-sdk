
# Set-Xdsitemetadata
Creates or updates metadata key-value pairs for a Site
## Syntax
```
Set-XDSiteMetadata -DataName <String> -DataValue <String> [-PassThru] [-AdminAddress <String>] [<CommonParameters>]
```
## Detailed Description
Creates or updates metadata key-value pairs for a Site which has a Controller identified by AdminAddress.


## Related Commands

* [Get-XDSite](./Get-XDSite/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| DataName | The name of the metadata member that is to be created/updated. | true | true (ByPropertyName) |  |
| DataValue | The value of the metadata member that is to be created/updated. | true | true (ByPropertyName) |  |
| PassThru | Returns the affected record. By default, this cmdlet does not generate any output. | false | false | False |
| AdminAddress | Specifies the address of the Delivery Controller to which the PowerShell module will connect. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |

## Input Type

### None
The DataName and DataValue parameters may be piped into this cmdlet by property name.
## Return Values

### None Or Citrix.Xendesktoppowershellsdk.Serviceinterfaces.Configuration.Site
This cmdlet does not generate any output, unless you use the PassThru parameter, in which case it generates a Citrix.XenDesktopPowerShellSdk.ServiceInterfaces.Configuration.Site object.
## Examples

### Example 1
```
Set-XDSiteMetadata -DataName "MyMetadataName" -DataValue "1234"
```
#### Description
Creates, or if it already exists, updates the metadata key "MyMetadataName" with the value "1234".
