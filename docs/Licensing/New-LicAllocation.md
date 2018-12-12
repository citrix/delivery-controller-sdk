
# New-Licallocation
Gets License Inventory Data from the License Server
## Syntax
```
New-LicAllocation [-AdminAddress] <String> -EntitlementId <String> -Count <Int32> -SessionId <String> [-CertHash <String>] [-Credentials <PSCredential>] [<CommonParameters>]
```
## Detailed Description
Returns detailed information about licenses in the inventory of the server pointed to by the snapin


## Related Commands

## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| AdminAddress | Specifies the Web Services for Licensing address of the License Server that the PowerShell Snap-in will connect to.  Retrieve this address with Get-LicLocation. | true | true (ByValue) |  |
| EntitlementId | Entitlement Id from which to allocate licenses. | true | false |  |
| Count | Number of licenses to allocate. | true | false | false |
| SessionId | SessionId from Get-LicEntitlements. | true | false | false |
| CertHash | Specifies the hash of the License Server certificate needing verification. | false | false |  |
| Credentials | Specifies the username/password to be authenticated with the License Server. | false | false |  |

## Input Type

### 

## Return Values

### 

## Notes
If the command fails, one of the following errors is returned.<br>    Error Codes<br>    -----------<br>    LicensingAdminStatus.UserNotAuthorized<br>        The currently authenticated user is not authorized to perform this operation.<br>    LicensingAdminStatus.CommunicationError<br>        There was a problem communicating with the License Server.<br>    LicensingAdminStatus.NoWriteAccess<br>        No write permission for writing license file.<br>    LicensingAdminStatus.LicenseWriteFailed<br>        Have write permission but license file could not be written.<br>    LicensingAdminStatus.InvalidEntitlementId<br>        The Entitlement ID specified is invalid.<br>    LicensingAdminStatus.InvalidSession<br>        The Session ID specified is invalid.<br>    LicensingAdminStatus.SessionExpired<br>        The Session ID specified has expired.<br>    LicensingAdminStatus.InvalidCount<br>        The license count specified is invalid.<br>    LicensingAdminStatus.UnknownError<br>        An unexpected error occurred.  For more details, see the Windows event logs on the controller.
## Examples

### Example 1
```
C:\PS>New-LicAllocation -AdminAddress https://licserver.mydomain.net:8083 -EntitlementId key002 -Count 10 -SessionId 551FL1YZ2KVPAQDZYXN1
```Allocates and downloads 10 licenses from citrix.com.
