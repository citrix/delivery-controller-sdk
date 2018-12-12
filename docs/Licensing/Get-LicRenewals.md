
# Get-Licrenewals
Enumerates the list of Customer Success Services renewal licenses available from citrix.com for the installed licenses
## Syntax
```
Get-LicRenewals [-AdminAddress] <String> [-CertHash <String>] [-Credentials <PSCredential>] [<CommonParameters>]
```
## Detailed Description
Returns detailed information about the Customer Success Services renewal licenses available for download and installation from Citrix.com


## Related Commands

## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| AdminAddress | Specifies the Web Services for Licensing address of the License Server to which the PowerShell Snap-in will connect.  Retrieve this address with Get-LicLocation. | true | true (ByValue) |  |
| CertHash | Specifies the hash of the License Server certificate needing verification. | false | true (ByValue) |  |
| Credentials | Specifies the username/password to be authenticated with the License Server. | false | false |  |

## Input Type

### System.String

## Return Values

### Citrix.Licensing.Admin.Sdk.Wslfulfillment\[\]

## Notes
If the command fails, one of the following errors is returned.<br>    Error Codes<br>    -----------<br>    LicensingAdminStatus.UserNotFound<br>         The specified Active Directory account or group could not be found.<br>    LicensingAdminStatus.UserNotAuthorized<br>         The currently authenticated user is not authorized to perform this operation.<br>    LicensingAdminStatus.NoSARenewals<br>         No Customer Success Services Renewal licenses available.<br>    LicensingAdminStatus.InvalidCertificate<br>         Invalid certificate Hash provided doesnt match with the server certificate hash. Get the Certificate using Get-LicCertificate cmdlet.<br>    LicensingAdminStatus.CertificateVerificationFailed<br>         Certificate is not verified or it is self-signed. Get the Certificate using Get-LicCertificate cmdlet and provide the hash for -CertHash parameter.<br>    LicensingAdminStatus.CommunicationError<br>         There was a problem communicating with the License Server.<br>    LicensingAdminStatus.UnknownError<br>         An unexpected error occurred.  For more details, see the Windows event logs on the controller.
## Examples

### Example 1
```
PS C:\>$cert = Get-LicCertificate -AdminAddress https://licserver.mydomain.net:8083

PS C:\Users\kamald> Get-LicRenewals -AdminAddress https://licserver.mydomain.net:8083 -CertHash $cert.CertHash
```Returns the list of Customer Success Services renewal licenses available for currently installed licenses in the License Server.&lt;br&gt;FulfillmentId               : FID-XD-Retail8-1003&lt;br&gt;ProductName                 : Citrix XenDesktop Platinum|User/Device&lt;br&gt;SerialNumber                : LA-XD-Retail8-20001:FID-XD-Retail8-1002&lt;br&gt;CustomerSuccessServicesDate : 01-01-0001 00:00:00&lt;br&gt;Quantity                    : 1
### Example 2
```
PS C:\>$cert = Get-LicCertificate -AdminAddress https://licserver.mydomain.net:8083

PS C:\Users\kamald> Get-LicRenewals -AdminAddress https://licserver.mydomain.net:8083 -CertHash $cert.CertHash
```Returns the list of Customer Success Services renewal licenses available for currently installed licenses in the License Server.&lt;br&gt;FulfillmentId               : FID-MPS-14&lt;br&gt;ProductName                 : Citrix XenApp (Presentation Server) Platinum|Concurrent User&lt;br&gt;SerialNumber                : LA-MPS-OR10:FID-MPS-13&lt;br&gt;CustomerSuccessServicesDate : 01-01-0001 00:00:00&lt;br&gt;Quantity                    : 1&lt;br&gt;FulfillmentId               : FID-XD-Retail8-1003&lt;br&gt;ProductName                 : Citrix XenDesktop Platinum|User/Device&lt;br&gt;SerialNumber                : LA-XD-Retail8-20001:FID-XD-Retail8-1002&lt;br&gt;CustomerSuccessServicesDate : 01-01-0001 00:00:00&lt;br&gt;Quantity                    : 1
