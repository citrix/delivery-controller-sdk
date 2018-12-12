
# Get-Licceipoption
Returns current CEIP option set on the License Server.
## Syntax
```
Get-LicCEIPOption [-AdminAddress] <String> [-CertHash <String>] [<CommonParameters>]
```
## Detailed Description
Returns the current CEIP(Customer Experience Improvement Program) option set on the License Server.


## Related Commands

* [Set-LicCEIPOption](./Set-LicCEIPOption/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| AdminAddress | Specifies the Web Services for Licensing address of the License Server that the PowerShell Snap-in will connect to.  Retrieve this address with Get-LicLocation. | true | true (ByValue) |  |
| CertHash | Specifies the hash of the License Server certificate needing verification. | false | false |  |

## Input Type

### System.String

## Return Values

### Citrix.Licensing.Admin.Sdk.Wslceipoption

## Notes
If the command fails, one of the following errors is returned.<br>            Error Codes<br>            -----------<br>            LicensingAdminStatus.CommunicationError<br>                There was a problem communicating with the License Server.<br>            LicensingAdminStatus.InvalidCertificate<br>                Certificate is not verified or it is self-signed. Get the Certificate and store the Hash in Ccs.<br>            LicensingAdminStatus.CertificateVerificationFailed<br>                Certificate is not verified or it is self-signed. Get the Certificate and store the Hash in Ccs.<br>            LicensingAdminStatus.UnknownError<br>                An unexpected error occurred.  For more details, see the Windows event logs on the controller.
## Examples

### Example 1
```
PS C:\>$cert = Get-LicCertificate -AdminAddress https://licserver.mydomain.net:8083

PS C:\> Get-LicCEIPOption -AdminAddress https://licserver.mydomain.net:8083 -CertHash $cert.CertHash
```Returns the CEIP option set on the License Server.&lt;br&gt;Output:&lt;br&gt;CEIPOption&lt;br&gt;----------&lt;br&gt;Diag
