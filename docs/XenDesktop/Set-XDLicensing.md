
# Set-Xdlicensing
Changes one or more of the licensing attributes of a Site
## Syntax
```
Set-XDLicensing [-Force] [-LicenseServerAddress <String>] [-LicenseServerPort <String>] [-LicensingModel <String>] [-PassThru] [-ProductCode <String>] [-ProductEdition <String>] [-AdminAddress <String>] [<CommonParameters>]
```
## Detailed Description
Changes one or more of the licensing attributes of the Site which has a Controller identified by AdminAddress. When the Citrix License Server address and/or port are specified and Force is not, the new server:port combination will be validated before being changed. Otherwise, no validation is performed.


## Related Commands

* [Get-ConfigLicensingModel](./Get-ConfigLicensingModel/)
* [Get-ConfigProductEdition](./Get-ConfigProductEdition/)
* [Get-XDLicensing](./Get-XDLicensing/)
* [Get-XDSite](./Get-XDSite/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| Force | Force the setting of the License Server address and/or port, i.e. do not check that the new server:port combination is valid. This can be used, for example, when the License Server needs to be set but is temporarily unavailable. | false | false |  |
| LicenseServerAddress | The address of the License Server for this Site. If this parameter is not provided then the License Server address will not be altered. | false | false |  |
| LicenseServerPort | The port on which the License Server for this Site is listening. If this parameter is not provided then the License Server port will not be altered. | false | false |  |
| LicensingModel | The licensing model for this Site. If this parameter is not provided then the licensing model will not be altered. Use the ProductCode returned from Get-XDSite as input to Get-ConfigLicensingModel to determine the list of valid licensing models. | false | false |  |
| PassThru | Returns the affected record. By default, this cmdlet does not generate any output. | false | false | False |
| ProductCode | The product code for this Site. If this parameter is not provided then the product code will not be altered. Find valid product codes by running Get-ConfigProduct. | false | false |  |
| ProductEdition | The product edition for this Site. If this parameter is not provided then the product edition will not be altered. Use the ProductCode returned from Get-XDSite as input to Get-ConfigProductEdition to determine the list of valid product editions. | false | false |  |
| AdminAddress | Specifies the address of the Delivery Controller to which the PowerShell module will connect. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |

## Input Type

### None
You cannot pipe input to this cmdlet.
## Return Values

### None Or Citrix.Xendesktoppowershellsdk.Serviceinterfaces.Configuration.Licenseinformation
This cmdlet does not generate any output, unless you use the PassThru parameter, in which case it generates a Citrix.XenDesktopPowerShellSdk.ServiceInterfaces.Configuration.LicenseInformation object.
## Notes
The command can fail for the following reasons:<br>    o The supplied License Server does not support the requested product edition.<br>    o A License Server was not found at the supplied address.
## Examples

### Example 1
```
C:\PS> Set-XDLicensing -AdminAddress MyController -LicenseServerAddress MyLicenseServer -LicenseServerPort 27001
```
#### Description
For the Site managed by MyController, changes the License Server to MyLicenseServer:27001.
