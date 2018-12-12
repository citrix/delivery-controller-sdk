
# Set-Licceipoption
Sets the CEIP option on the License Server.
## Syntax
```
Set-LicCEIPOption [-AdminAddress] <String> -CEIPOption <String> [-CertHash <String>] [-Credentials <PSCredential>] [<CommonParameters>]
```
## Detailed Description
Sets the CEIP(Customer Experience Improvement Program) option on the License Server.


## Related Commands

* [Get-LicCEIPOption](./Get-LicCEIPOption/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| AdminAddress | Specifies the Web Services for Licensing address of the License Server that the PowerShell Snap-in will connect to.  Retrieve this address with Get-LicLocation. | true | true (ByValue) |  |
| CEIPOption | Specifies the CEIP option to be set on the License Server. Allowed Values are None, Anonymous and Diagnostic. | true | false |  |
| CertHash | Specifies the hash of the License Server certificate needing verification. | false | false |  |
| Credentials | Specifies the username/password to be authenticated with the License Server. | false | false |  |

## Input Type

### System.String

## Return Values

### None

## Notes
If the command fails, one of the following errors is returned.<br>    Error Codes<br>    -----------<br>    LicensingAdminStatus.CommunicationError<br>        There was a problem communicating with the License Server.<br>    LicensingAdminStatus.InvalidCertificate<br>        Certificate is not verified or it is self-signed. Get the Certificate and store the Hash in Ccs.<br>    LicensingAdminStatus.CertificateVerificationFailed<br>        Certificate is not verified or it is self-signed. Get the Certificate and store the Hash in Ccs.<br>    LicensingAdminStatus.AuthorizationFailed<br>         Authentication and authorization failed for the given UserName password<br>    LicensingAdminStatus.InvalidCEIPOption<br>         Invalid CEIP Option. Allowed Values are None, Anonymous and Diagnostic.<br>    LicensingAdminStatus.UnknownError<br>                An unexpected error occurred.  For more details, see the Windows event logs on the controller.
## Examples

### Example 1
```
PS C:\> $cert = Get-LicCertificate -AdminAddress https://licserver.mydomain.net:8083

PS C:\> Set-LicCEIPOption -AdminAddress https://licserver.mydomain.net:8083 -CertHash $cert.CertHash -CEIPOption Diagnostic
```Sets the CEIP option to 'Diagnostic' for sending Licensing Server usage information.
