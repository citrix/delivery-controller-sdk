
# Install-Licrenewals
Download and Install the Customer Success Services Renewal Licenses using Citrix.com
## Syntax
```
Install-LicRenewals [-AdminAddress] <String> -FulfillmentID <String> [-CertHash <String>] [-Credentials <PSCredential>] [<CommonParameters>]
```
## Detailed Description
Download and Install the Customer Success Services Renewal Licenses for the specified Fulfillment ID using Citrix.com


## Related Commands

## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| AdminAddress | Specifies the Web Services for Licensing address of the License Server that the PowerShell Snap-in will connect to.  Retrieve this address with Get-LicLocation. | true | true (ByValue) |  |
| FulfillmentID | Fulfillment ID for which the licenses need to be downloaded and installed. | true | false |  |
| CertHash | Specifies the hash of the License Server certificate needing verification. | false | false |  |
| Credentials | Specifies the username/password to be authenticated with the License Server. | false | false |  |

## Input Type

### System.String

## Return Values

### 

## Notes
If the command fails, one of the following errors is returned.<br>    Error Codes<br>    -----------<br>    LicensingAdminStatus.UserNotFound<br>        The specified Active Directory account or group was not found.<br>    LicensingAdminStatus.UserNotAuthorized<br>        The currently authenticated user is not authorized to perform this operation.<br>    LicensingAdminStatus.NoRenewalLicenseFound<br>        No Customer Success Services Renewal licenses found for the specified FulfillmentID.<br>    LicensingAdminStatus.InvalidCertificate<br>        Invalid certificate Hash provided doesnt match with the server certificate hash. Get the Certificate using Get-LicCertificate cmdlet.<br>    LicensingAdminStatus.CertificateVerificationFailed<br>        Certificate is not verified or it is self-signed. Get the Certificate using Get-LicCertificate cmdlet and provide the hash for -CertHash parameter.<br>    LicensingAdminStatus.CommunicationError<br>        There was a problem communicating with the License Server.<br>    LicensingAdminStatus.UnknownError<br>        An unexpected error occurred.  For more details, see the Windows event logs on the controller.
## Examples

### Example 1
```
PS C:\>$cert = Get-LicCertificate -AdminAddress https://licserver.mydomain.net:8083

PS C:\> $fulfillments = Get-LicRenewals -AdminAddress https://licserver.mydomain.net:8083 -CertHash $cert.CertHash

PS C:\> Install-LicRenewals -AdminAddress https://licserver.mydomain.net:8083 -CertHash $cert.CertHash -FulfillmentID $fulfillments[0].FulfillmentId
```Download and Install the Customer Success Services Renewal Licenses.
