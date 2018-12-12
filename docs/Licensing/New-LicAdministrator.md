
# New-Licadministrator
Adds an Active Directory account or group to the list of administrators on the License Server.
## Syntax
```
New-LicAdministrator [-AdminAddress] <String> -Account <String> [-Group] [-ReadOnly] [-CertHash <String>] [-Credentials <PSCredential>] [<CommonParameters>]
```
## Detailed Description
Adds the specified domain-qualified Active Directory account or group to the list of administrators for the License Server.  If the ReadOnly parameter is included, the account is added with read-only administrative permission;  otherwise, the account is added with full administrative permission.  If the specified account is already on the list, no change is made.

By default, all members of the BUILTIN\\Administrators group on the License Server, and the user who installed the License Server, automatically have full administrative permission.


## Related Commands

* [Get-LicAdministrator](./Get-LicAdministrator/)
* [Remove-LicAdministrator](./Remove-LicAdministrator/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| AdminAddress | Specifies the Web Services for Licensing address of the License Server that the PowerShell Snap-in will connect to.  Retrieve this address with Get-LicLocation. | true | true (ByValue) |  |
| Account | Specifies the Active Directory account or group to be added as an administrator of the License Server.  The account must be specified in domain-qualified format, that is, &lt;Domain&gt;\\&lt;Account&gt; or &lt;Account&gt;@&lt;Domain&gt;. | true | false |  |
| Group | Specifies that the account name supplied is a Group. | false | false |  |
| ReadOnly | Specifies that the account should have read-only permission. | false | false |  |
| CertHash | Specifies the hash of the License Server certificate needing verification. | false | false |  |
| Credentials | Specifies the username/password to be authenticated with the License Server. | false | false |  |

## Input Type

### 

## Return Values

### Citrix.Licensing.Admin.Sdk.Wsluser

## Notes
If the command fails, one of the following errors is returned.<br>    Error Codes<br>    -----------<br>    ActiveDirectoryAccountResolutionFailed<br>        The specified Active Directory account or group could not be found.<br>    LicensingAdminStatus.UserNotAuthorized<br>        The currently authenticated user is not authorized to perform this operation.<br>    LicensingAdminStatus.CommunicationError<br>        There was a problem communicating with the License Server.<br>    LicensingAdminStatus.UnknownError<br>        An unexpected error occurred.  For more details, see the Windows event logs on the controller.
## Examples

### Example 1
```
C:\PS>New-LicAdministrator -AdminAddress https://licserver.mydomain.net:8083 -Account "mydomain\Domain Admins" -Group

Account                AccountSid                                       Group       Permissions

-------                ----------                                       -----       -----------

mydomain\Domain Admins S-1-5-21-1315084875-1285793635-512               True        Full
```Adds all domain admins in the domain named 'mydomain' to the list of full administrators for the specified License Server.
### Example 2
```
C:\PS>New-LicAdministrator -AdminAddress https://licserver.mydomain.net:8083 -Account "mydomain\Domain Users" -Group -ReadOnly

Account                AccountSid                                       Group       Permissions

-------                ----------                                       -----       -----------

mydomain\Domain Users  S-1-5-21-1315084875-1285793635-513               True        ReadOnly
```Adds all domain users in the domain named 'mydomain' to the list of read-only administrators for the specified License Server.
