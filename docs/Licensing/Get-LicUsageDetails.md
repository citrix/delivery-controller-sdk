
# Get-Licusagedetails
Gets the license usage details for the requested Product Edition Model. Currently it shows only usage details for User/Device model only.
## Syntax
```
Get-LicUsageDetails [-AdminAddress] <String> -ProductEditionModel <String> [-CertHash <String>] [<CommonParameters>]
```
## Detailed Description
Returns the list of license usage details for the requested P\_E\_M Product Edition Model String. Currently it shows only usage details for the User/Device model only.


## Related Commands

## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| AdminAddress | Specifies the Web Services for Licensing address of the License Server that the PowerShell Snap-in will connect to.  Retrieve this address with Get-LicLocation. | true | true (ByValue) |  |
| ProductEditionModel | Specifies the P\_E\_M Product Edition Model String for which license usage details are requested. | true | false |  |
| CertHash | Specifies the hash of the License Server certificate needing verification. | false | false |  |

## Input Type

### System.String

## Return Values

### Citrix.Licensing.Admin.Sdk.Wslusagedetails\[\]

## Notes
If the command fails, one of the following errors is returned.<br>            Error Codes<br>            -----------<br>            LicensingAdminStatus.CommunicationError<br>                There was a problem communicating with the License Server.<br>            LicensingAdminStatus.InvalidCertificate<br>                Certificate is not verified or it is self-signed. Get the Certificate and store the Hash in Ccs.<br>            LicensingAdminStatus.CertificateVerificationFailed<br>                Certificate is not verified or it is self-signed. Get the Certificate and store the Hash in Ccs.<br>            LicensingAdminStatus.UnknownError<br>                An unexpected error occurred.  For more details, see the Windows event logs on the controller.
## Examples

### Example 1
```
PS C:\> $cert = Get-LicCertificate -AdminAddress https://licserver.mydomain.net:8083

PS C:\> $usgdetails = Get-LicUsageDetails -AdminAddress https://licserver.mydomain.net:8083 -ProductEditionModel XDT_PLT_UD -CertHash $cert.CertHash
```Returns the list of license usage details for the XDT\_PLT\_UD (Product Edition Model) string from the License Server on licserver.mydomain.net.&lt;br&gt;Output:&lt;br&gt;PS C:\\&gt;  \$usgdetails\[0\]&lt;br&gt;PEM               SADate           LicenseModelType        Name&lt;br&gt;---               ------           ----------------        ----&lt;br&gt;XDT\_PLT\_UD        2015.1201        Device                  device00000001
