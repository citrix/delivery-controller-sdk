
# Get-Licentitlements
Enumerates the set of licenses associated with a License Access Code via citrix.com.
## Syntax
```
Get-LicEntitlements [-AdminAddress] <String> -AccessCode <String> [-CertHash <String>] [-Credentials <PSCredential>] [<CommonParameters>]
```
## Detailed Description
Returns detailed information about the licenses associated with the specified License Access Code with citrix.com.


## Related Commands

## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| AdminAddress | Specifies the Web Services for Licensing address of the License Server that the PowerShell Snap-in will connect to.  Retrieve this address with Get-LicLocation. | true | true (ByValue) |  |
| AccessCode | License Access Code. | true | false |  |
| CertHash | Specifies the hash of the License Server certificate needing verification. | false | false |  |
| Credentials | Specifies the username/password to be authenticated with the License Server. | false | false |  |

## Input Type

### 

## Return Values

### Citrix.Licensing.Admin.Sdk.Wslentitlements\[\]

## Notes
If the command fails, one of the following errors is returned.<br>    Error Codes<br>    -----------<br>    LicensingAdminStatus.UserNotFound<br>        The specified Active Directory account or group could not be found.<br>    LicensingAdminStatus.UserNotAuthorized<br>        The currently authenticated user is not authorized to perform this operation.<br>    LicensingAdminStatus.CommunicationError<br>        There was a problem communicating with the License Server.<br>    LicensingAdminStatus.UnknownError<br>        An unexpected error occurred.  For more details, see the Windows event logs on the controller.
## Examples

### Example 1
```
C:\PS>Get-LicEntitlements -AdminAddress https://licserver.mydomain.net:8083 -AccessCode LA-0000431065-00000
```Queries the server https://licserver.mydomain.net:8083 for the License Data in its inventory&lt;br&gt;Output:&lt;br&gt;EntitlementSessionId               : 551FL1YZ2KVPAQDZYXN1&lt;br&gt;EntitlementId                      : key002&lt;br&gt;EntitlementProductName             :  Citrix XenServer Platinum Edition&lt;br&gt;EntitlementRelevance               : 0&lt;br&gt;LicenseBindType                    : HOSTNAME&lt;br&gt;LicensesTotal                      : 100&lt;br&gt;LicensesAvailable                  : 100&lt;br&gt;EntitlementPurchaseDate            : 12/1/2010 12:00:00 AM&lt;br&gt;EntitlementCustomerSuccessServices : 12/1/2010 12:00:00 AM&lt;br&gt;EntitlementExpiryDate              : 1/1/2013 12:00:00 AM&lt;br&gt;FeatureList                        : {, , }&lt;br&gt;EntitlementSessionId               : 551FL1YZ2KVPAQDZYXN1&lt;br&gt;EntitlementId                      : key003&lt;br&gt;EntitlementProductName             :  Citrix Access Gateway and Advanced Access Control - With Customer Success Services&lt;br&gt;EntitlementRelevance               : 0&lt;br&gt;LicenseBindType                    : HOSTNAME&lt;br&gt;LicensesTotal                      : 100&lt;br&gt;LicensesAvailable                  : 100&lt;br&gt;EntitlementPurchaseDate            : 12/1/2010 12:00:00 AM&lt;br&gt;EntitlementCustomerSuccessServices : 12/1/2010 12:00:00 AM&lt;br&gt;EntitlementExpiryDate              : 1/1/2013 12:00:00 AM&lt;br&gt;FeatureList                        : {, }
