
# Get-Licconfigusagesamples
Returns current configuration for sample collection on license usages.
## Syntax
```
Get-LicConfigUsageSamples [-AdminAddress] <String> [-CertHash <String>] [<CommonParameters>]
```
## Detailed Description
Returns the configuration stored on License Server for a sample collection about licenses usages.


## Related Commands

* [Set-LicConfigUsageSamples](./Set-LicConfigUsageSamples/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| AdminAddress | Specifies the Web Services for Licensing address of the License Server that the PowerShell Snap-in will connect to.  Retrieve this address with Get-LicLocation. | true | true (ByValue) |  |
| CertHash | Specifies the hash of the License Server certificate needing verification. | false | false |  |

## Input Type

### System.String

## Return Values

### Citrix.Licensing.Admin.Sdk.Wslconfigusagesample

## Notes
If the command fails, one of the following errors is returned.<br>            Error Codes<br>            -----------<br>            LicensingAdminStatus.CommunicationError<br>                There was a problem communicating with the License Server.<br>            LicensingAdminStatus.InvalidCertificate<br>                Certificate is not verified or it is self-signed. Get the Certificate and store the Hash in Ccs.<br>            LicensingAdminStatus.CertificateVerificationFailed<br>                Certificate is not verified or it is self-signed. Get the Certificate and store the Hash in Ccs.<br>            LicensingAdminStatus.UnknownError<br>                An unexpected error occurred.  For more details, see the Windows event logs on the controller.
## Examples

### Example 1
```
PS C:\>$cert = Get-LicCertificate -AdminAddress https://licserver.mydomain.net:8083

PS C:\> Get-LicConfigUsageSamples -AdminAddress https://licserver.mydomain.net:8083 -CertHash $cert.CertHash
```Returns the configuration for sample usage collection on the License Server.&lt;br&gt;Output:&lt;br&gt;Enabled            : True&lt;br&gt;PollingInterval    : 15&lt;br&gt;RetentionPeriod    : 180&lt;br&gt;EarliestSampleTime : 1/30/2015 7:51:20 AM&lt;br&gt;LatestSampleTime   : 2/5/2015 9:08:08 AM&lt;br&gt;Note:&lt;br&gt;PollingInterval   (in minutes)&lt;br&gt;RetentionPeriod (in days)
### Example 2
```
PS C:\>$cert = Get-LicCertificate -AdminAddress https://licserver.mydomain.net:8083

PS C:\> Get-LicConfigUsageSamples -AdminAddress https://licserver.mydomain.net:8083 -CertHash $cert.CertHash
```Returns  the configuration for sample usage collection on the License Server.&lt;br&gt;Output:&lt;br&gt;Enabled            : False&lt;br&gt;PollingInterval    :&lt;br&gt;RetentionPeriod    :&lt;br&gt;EarliestSampleTime : 1/30/2015 7:51:20 AM&lt;br&gt;LatestSampleTime   : 2/5/2015 9:08:08 AM&lt;br&gt;Note:&lt;br&gt;PollingInterval   (in minutes)&lt;br&gt;RetentionPeriod (in days)
