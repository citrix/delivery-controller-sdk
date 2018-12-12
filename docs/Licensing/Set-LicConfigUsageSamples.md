
# Set-Licconfigusagesamples
Sets the configuration to collect samples of license usage
## Syntax
```
Set-LicConfigUsageSamples [-AdminAddress] <String> [-Enable <Boolean>] [-PollingInterval <Int32>] [-RetentionPeriod <Int32>] [-CertHash <String>] [-Credentials <PSCredential>] [<CommonParameters>]
```
## Detailed Description
Sets the configuration stored on the License Server to collect samples of licenses usage/consumption.


## Related Commands

* [Get-LicConfigUsageSamples](./Get-LicConfigUsageSamples/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| AdminAddress | Specifies the Web Services for Licensing address of the License Server that the PowerShell Snap-in will connect to.  Retrieve this address with Get-LicLocation. | true | true (ByValue) |  |
| Enable | To enable or disable the sample collection. | false | false |  |
| PollingInterval | Specifies the Polling period (in minutes) for sample collection. Recommended polling period is 15 minutes. You can configure any polling period. Minimum is 5 minutes to reduce the load on License Server. Maximum is 1440 minutes (that is, 1 day). | false | false |  |
| RetentionPeriod | Specifies the retention period (in days) for license usage samples. The recommended retention period is 180 days. You can configure any retention period. Minimum is 30 days. | false | false |  |
| CertHash | Specifies the hash of the License Server certificate needing verification. | false | false |  |
| Credentials | Specifies the username/password to be authenticated with the License Server. | false | false |  |

## Input Type

### System.String

## Return Values

### None

## Notes
If the command fails, one of the following errors is returned.<br>            Error Codes<br>            -----------<br>            LicensingAdminStatus.CommunicationError<br>                There was a problem communicating with the License Server.<br>            LicensingAdminStatus.InvalidCertificate<br>                Certificate is not verified or it is self-signed. Get the Certificate and store the Hash in Ccs.<br>            LicensingAdminStatus.CertificateVerificationFailed<br>                Certificate is not verified or it is self-signed. Get the Certificate and store the Hash in Ccs.<br>            LicensingAdminStatus.AuthorizationFailed<br>                Authentication and authorization failed for the given UserName password<br>    		    LicensingAdminStatus.PollingIntervalMoreThanMaxValue<br>                Polling Interval is more than allowed maximum value(1440 minutes = 1 day).<br>    		    LicensingAdminStatus.PollingIntervalLessThanMinValue<br>                Polling Interval is less than allowed minimum value(5 minuets).<br>            LicensingAdminStatus.RetentionPeriodLessThanMinValue<br>                Retention Period is less than allowed minimum value(30 days).<br>            LicensingAdminStatus.UnknownError<br>                An unexpected error occurred.  For more details, see the Windows event logs on the controller.
## Examples

### Example 1
```
PS C:\> $cert = Get-LicCertificate -AdminAddress https://licserver.mydomain.net:8083

PS C:\> Set-LicConfigUsageSamples -AdminAddress https://licserver.mydomain.net:8083 -CertHash $cert.CertHash -Enable $false -PollingInterval 20 -RetentionPeriod 190
```Enables the sample collection of license usage on the License Server with a polling interval of 20 minutes  and retention period of 190 days.
### Example 2
```
PS C:\>$cert = Get-LicCertificate -AdminAddress https://licserver.mydomain.net:8083

PS C:\> Set-LicConfigUsageSamples -AdminAddress https://licserver.mydomain.net:8083 -CertHash $cert.CertHash -Enable $false
```Disables the sample collection of license usage on the License Server.
### Example 3
```
PS C:\> $cert = Get-LicCertificate -AdminAddress https://licserver.mydomain.net:8083

PS C:\> Set-LicConfigUsageSamples -AdminAddress https://licserver.mydomain.net:8083 -CertHash $cert.CertHash -Enable $true -PollingInterval 30
```Enables the sample collection of license usage on the License Server with a polling interval of 30 minutes.
