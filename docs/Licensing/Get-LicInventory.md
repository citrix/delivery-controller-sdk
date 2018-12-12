
# Get-Licinventory
Gets License Inventory Data from the License Server
## Syntax
```
Get-LicInventory [-AdminAddress] <String> [-CheckForSameSerialNumber] [-Locale <String>] [-CertHash <String>] [-Credentials <PSCredential>] [<CommonParameters>]
```
## Detailed Description
Returns detailed information about licenses in the inventory of the server pointed to by the snapin


## Related Commands

## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| AdminAddress | Specifies the Web Services for Licensing address of the License Server that the PowerShell Snap-in will connect to.  Retrieve this address with Get-LicLocation. | true | true (ByValue) |  |
| CheckForSameSerialNumber | Switch if present filters the Inventory result. | false | false | False |
| Locale | Language code of localized human readable strings. | false | false | EN |
| CertHash | Specifies the hash of the License Server certificate needing verification. | false | false |  |
| Credentials | Specifies the username/password to be authenticated with the License Server. | false | false |  |

## Input Type

### 

## Return Values

### Citrix.Licensing.Admin.Sdk.Wslinventory\[\]

## Notes
If the command fails, one of the following errors is returned.<br>    Error Codes<br>    -----------<br>    LicensingAdminStatus.UserNotAuthorized<br>        The currently authenticated user is not authorized to perform this operation.<br>    LicensingAdminStatus.CommunicationError<br>        There was a problem communicating with the License Server.<br>    LicensingAdminStatus.CitrixLicensingVendorOrServiceDown<br>        The Vendor Daemon or Service is down or unresponsive.<br>    LicensingAdminStatus.NoInventory<br>        There was no available inventory on the specified License Server.<br>    LicensingAdminStatus.LocaleUnsupported<br>        The locale specified is not supported.<br>    LicensingAdminStatus.UnknownError<br>        An unexpected error occurred.  For more details, see the Windows event logs on the controller.
## Examples

### Example 1
```
C:\PS>Get-LicInventory -AdminAddress https://licserver.mydomain.net:8083
```Queries the server https://licserver.mydomain.net:8083 for the License Data in its inventory&lt;br&gt;Output:&lt;br&gt;LicenseProductName                 : CITRIX&lt;br&gt;LocalizedLicenseProductName        : Citrix Start-up License&lt;br&gt;LicenseEdition                     :&lt;br&gt;LicenseLocalizedEdition            :&lt;br&gt;LicenseExpirationDate              : 12/31/1999 7:00:00 PM&lt;br&gt;LicenseCustomerSuccessServicesDate : 12/31/2037 7:00:00 PM&lt;br&gt;LicenseType                        : SYS&lt;br&gt;LocalizedLicenseType               : System&lt;br&gt;LicensesInUse                      : 0&lt;br&gt;LicensesAvailable                  : 4000&lt;br&gt;LicenseOverdraft                   : 0&lt;br&gt;LicenseModel                       :&lt;br&gt;LocalizedLicenseModel              : Server&lt;br&gt;LicenseProductName                 : MPS&lt;br&gt;LocalizedLicenseProductName        : Citrix XenApp (Presentation Server) Platinum&lt;br&gt;LicenseEdition                     : PLT&lt;br&gt;LicenseLocalizedEdition            :&lt;br&gt;LicenseExpirationDate              : 11/30/2011 7:00:00 PM&lt;br&gt;LicenseCustomerSuccessServicesDate : 11/30/2001 7:00:00 PM&lt;br&gt;LicenseType                        : Retail&lt;br&gt;LocalizedLicenseType               : Retail&lt;br&gt;LicensesInUse                      : 0&lt;br&gt;LicensesAvailable                  : 0&lt;br&gt;LicenseOverdraft                   : 0&lt;br&gt;LicenseModel                       : CCU&lt;br&gt;LocalizedLicenseModel              : Concurrent User
