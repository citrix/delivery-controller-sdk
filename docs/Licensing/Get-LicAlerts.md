
# Get-Licalerts
Get Active Alerts on the License Server
## Syntax
```
Get-LicAlerts [-AdminAddress] <String> -ProductEditionModel <String> -SADate <String> [-FilterThreshold <Int32>] [-MetaData <String>] [-Locale <String>] [-CertHash <String>] [<CommonParameters>]
```
## Detailed Description
Gets the alerts active on the License Server for the given Product Edition Model and required Customer Success Services date. Returns the alert list of message strings in requested locale.


## Related Commands

## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| AdminAddress | Specifies the Web Services for Licensing address of the License Server that the PowerShell Snap-in will connect to.  Retrieve this address with Get-LicLocation. | true | true (ByValue) |  |
| ProductEditionModel | The P\_E\_M Product Edition Model String for which Alerts are requested. | true | false |  |
| SADate | The required Customer Success Services date of the product. | true | false |  |
| FilterThreshold | Threshold for license usage expressed in percentage, some alert notifications are included only if license usage is above this threshold. | false | false |  |
| MetaData | Optional Data Client might need included in response for its internal purposes. | false | false |  |
| Locale | Language code of localized human-readable strings. | false | false |  |
| CertHash | Specifies the hash of the License Server certificate needing verification. | false | false |  |

## Input Type

### 

## Return Values

### Citrix.Licensing.Admin.Sdk.Wslalertmessages

## Notes
If the command fails, one of the following errors is returned.<br>    Error Codes<br>    -----------<br>    LicensingAdminStatus.Success<br>        Succesfully Imported the File to License Server<br>    LicensingAdminStatus.InvalidSADateFormat<br>        The required Customer Success Services date format is incorrect<br>    LicensingAdminStatus.CommunicationError<br>        There was a problem communicating with the License Server.<br>    LicensingAdminStatus.UnknownError<br>        An unexpected error occurred.  For more details, see the Windows event logs on the controller.
## Examples

### Example 1
```
PS C:\> $cert = Get-LicCertificate -AdminAddress https://licserver.mydomain.net:8083

PS C:\> $alerts = Get-LicAlerts -AdminAddress https://licserver.mydomain.net:8083 -ProductEditionModel "XDT_PLT_CCS" -SADate "2013.0123" -FilterThreshold 90 -CertHash $cert.CertHash

PS C:\> $alerts.AlertList[0].Description

Title                                      Detail                                  Action

-----                                      ------                                  ------

Customer Success Services does not supp... This product version is not supporte... Renew the licenses (Customer Succ...
```Gets alerts active on the License Server for product XDT Platinum edition Concurrent model with required Customer Success Services date 2013.0123 filtered with a usage threshold of 90%
