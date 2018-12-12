
# Set-Licsarenewaloptions
Sets the Customer Success Services renewal license check option on the License Server.
## Syntax
```
Set-LicSARenewalOptions [-AdminAddress] <String> -Option <String> [-CertHash <String>] [-Credentials <PSCredential>] [<CommonParameters>]
```
## Detailed Description
Sets the Customer Success Services renewal license check option on the License Server.


## Related Commands

## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| AdminAddress | Specifies the Web Services for Licensing address of the License Server that the PowerShell Snap-in will connect to.  Retrieve this address with Get-LicLocation. | true | true (ByValue) |  |
| Option | Specifies the Customer Success Services Renewal check option to be set on the License Server. Allowed Values are Notify, Install and Manual. | true | false |  |
| CertHash | Specifies the hash of the License Server certificate needing verification. | false | false |  |
| Credentials | Specifies the username/password to be authenticated with the License Server. | false | false |  |

## Input Type

### System.String

## Return Values

### 

## Notes
If the command fails, one of the following errors is returned.<br>    Error Codes<br>    -----------<br>    LicensingAdminStatus.CommunicationError<br>        There was a problem communicating with the License Server.<br>    LicensingAdminStatus.InvalidCertificate<br>        Invalid certificate Hash provided doesnt match with the server certificate hash. Get the Certificate using Get-LicCertificate cmdlet.<br>    LicensingAdminStatus.CertificateVerificationFailed<br>        Certificate is not verified or it is self-signed. Get the Certificate using Get-LicCertificate cmdlet and provide the hash for -CertHash parameter.<br>    LicensingAdminStatus.AuthorizationFailed<br>         Authentication and authorization failed for the given UserName password<br>    LicensingAdminStatus.InvalidSARenewalOption<br>         Invalid Customer Success Services renewal check Option. Allowed values are Notify, Install and Manual.<br>    LicensingAdminStatus.UnknownError<br>                An unexpected error occurred.  For more details, see the Windows event logs on the controller.
## Examples

### Example 1
```
PS C:\>$cert = Get-LicCertificate -AdminAddress https://licserver.mydomain.net:8083

PS C:\>Set-LicSARenewalOptions -AdminAddress https://licserver.mydomain.net:8083 -CertHash $cert.CertHash -Option Notify
```
