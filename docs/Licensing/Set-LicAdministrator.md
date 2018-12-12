
# Set-Licadministrator
Sets the permission level of the specified License Server administrator.
## Syntax
```
Set-LicAdministrator [-AdminAddress] <String> [-Account <String>] [-AccountSid <String>] [-Group] [-ReadOnly] [-CertHash <String>] [-Credentials <PSCredential>] [<CommonParameters>]
```
## Detailed Description
By default, all members of the BUILTIN\\Administrators group on the License Server, and the user who installed the License Server, automatically have full administrative permission.


## Related Commands

* [Get-LicAdministrator](./Get-LicAdministrator/)
* [Remove-LicAdministrator](./Remove-LicAdministrator/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| AdminAddress | Specifies the Web Services for Licensing address of the License Server that the PowerShell Snap-in will connect to.  Retrieve this address with Get-LicLocation. | true | true (ByValue) |  |
| Account | Specifies the Active Directory account or group for which permission to the License Server should be modified.  The account must be specified in domain-qualified format, that is, &lt;Domain&gt;\\&lt;Account&gt; or &lt;Account&gt;@&lt;Domain&gt;. | false | false |  |
| AccountSid | Specifies the security identifier of the account for which permission to the License Server should be modified, in security descriptor definition language form, for example, S-1-5-21-3207821160-2749172716-209583687-3116639481-3523051251. | false | false |  |
| Group | Specifies that the account name supplied is a Group. | false | false |  |
| ReadOnly | Specifies that the account should have read-only permission. | false | false |  |
| CertHash | Specifies the hash of the License Server certificate needing verification. | false | false |  |
| Credentials | Specifies the username/password to be authenticated with the License Server. | false | false |  |

## Input Type

### 

## Return Values

### Citrix.Licensing.Admin.Sdk.Wsluser

## Notes
If the command fails, one of the following errors is returned.<br>    Error Codes<br>    -----------<br>    LicensingAdminStatus.UserNotFound<br>        The specified Active Directory account or group could not be found.<br>    LicensingAdminStatus.UserNotAuthorized<br>        The currently authenticated user is not authorized to perform this operation.<br>    LicensingAdminStatus.CommunicationError<br>        There was a problem communicating with the License Server.<br>    LicensingAdminStatus.UnknownError<br>        An unexpected error occurred.  For more details, see the Windows event logs on the controller.
## Examples

### Example 1
```
C:\PS>Set-LicAdministrator -AdminAddress https://licserver.mydomain.net:8083 -Account mydomain\testuser1

Account                AccountSid                                       Group      Permissions

-------                ----------                                       -----      -----------

mydomain\testuser1     S-1-5-21-1315084875-1285793635-24181...          False      Full
```Sets the permission of testuser1 in the domain named 'mydomain' to full administrator for the specified License Server.
### Example 2
```
C:\PS>Set-LicAdministrator -AdminAddress https://licserver.mydomain.net:8083 -Account "mydomain\Domain users" -Group -ReadOnly

Account                AccountSid                                       Group      Permissions

-------                ----------                                       -----      -----------

mydomain\Domain Users  S-1-5-21-1315084875-1285793635-513               True       ReadOnly
```Sets the permission of all domain users in the domain named 'mydomain' to ReadOnly for the specified License Server.
