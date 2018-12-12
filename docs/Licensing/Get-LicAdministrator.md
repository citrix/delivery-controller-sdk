
# Get-Licadministrator
Gets a list of administrator accounts configured to access the License Server.
## Syntax
```
Get-LicAdministrator [-AdminAddress] <String> [-AccountSid <String>] [-ReadOnly] [-CertHash <String>] [-Credentials <PSCredential>] [<CommonParameters>]
```
## Detailed Description
Returns a list of administrator accounts currently configured to access the License Server.  If the ReadOnly parameter is included, only read-only accounts are returned; otherwise, all administrator accounts are returned.


## Related Commands

* [New-LicAdministrator](./New-LicAdministrator/)
* [Remove-LicAdministrator](./Remove-LicAdministrator/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| AdminAddress | Specifies the Web Services for Licensing address of the License Server that the PowerShell Snap-in will connect to.  Retrieve this address with Get-LicLocation. | true | true (ByValue) |  |
| AccountSid | Specifies the security identifier of the account to be located, in security descriptor definition language form (for example, S-1-5-21-3207821160-2749172716-209583687-3116639481-3523051251). | false | false |  |
| ReadOnly | Specifies that only administrator accounts with read-only permissions should be returned. | false | false |  |
| CertHash | Specifies the hash of the License Server certificate needing verification. | false | false |  |
| Credentials | Specifies the username/password to be authenticated with the License Server. | false | false |  |

## Input Type

### 

## Return Values

### Citrix.Licensing.Admin.Sdk.Wsluser

## Notes
If the command fails, one of the following errors is returned.<br>    Error Codes<br>    -----------<br>    LicensingAdminStatus.NoUsers<br>        No Licensing Administrators were found.<br>    LicensingAdminStatus.UserNotAuthorized<br>        The currently authenticated user is not authorized to perform this operation.<br>    LicensingAdminStatus.CommunicationError<br>        There was a problem communicating with the License Server.<br>    LicensingAdminStatus.InvalidFilter<br>        A filtering expression was included that could not be interpreted for this command.<br>    LicensingAdminStatus.UnknownError<br>        An unexpected error occurred.  For more details, see the Windows event logs on the controller.
## Examples

### Example 1
```
C:\PS>Get-LicAdministrator -AdminAddress https://licserver.mydomain.net:8083

Account                AccountSid                                       Group       Permissions

-------                ----------                                       -----       -----------

MYDOMAIN\testuser1     S-1-5-21-1315084875-1285793635-24181...          False       Full

MYDOMAIN\Domain Users  S-1-5-21-1315084875-1285793635-513               True        ReadOnly
```Gets all the administrator accounts and associated permissions for the specified License Server.
### Example 2
```
C:\PS>Get-LicAdministrator -AdminAddress https://licserver.mydomain.net:8083 -ReadOnly

Account                AccountSid                                       Group       Permissions

-------                ----------                                       -----       -----------

MYDOMAIN\Domain Users  S-1-5-21-1315084875-1285793635-513               True        ReadOnly
```Gets all administrator accounts with read-only permissions for the specified License Server.
