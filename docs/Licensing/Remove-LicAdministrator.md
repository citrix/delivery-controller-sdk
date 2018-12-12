
# Remove-Licadministrator
Removes an Active Directory account or group from the list of administrators on the License Server.
## Syntax
```
Remove-LicAdministrator [-AdminAddress] <String> [-Account] <String> [-CertHash <String>] [-Credentials <PSCredential>] [<CommonParameters>]

Remove-LicAdministrator [-AdminAddress] <String> -AccountSid <String> [-CertHash <String>] [-Credentials <PSCredential>] [<CommonParameters>]
```
## Detailed Description
Enables Active Directory accounts and groups to be removed from the list of administrators with permissions to access the License Server.


## Related Commands

* [New-LicAdministrator](./New-LicAdministrator/)
* [Get-LicAdministrator](./Get-LicAdministrator/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| AdminAddress | Specifies the Web Services for Licensing address of the License Server that the PowerShell Snap-in will connect to.  Retrieve this address with Get-LicLocation. | true | true (ByValue) |  |
| Account | Specifies the Active Directory account or group to be removed from the list of administrators from the License Server.  The account must be specified in domain-qualified format, that is, &lt;Domain&gt;\\&lt;Account&gt; or &lt;Account&gt;@&lt;Domain&gt;. | true | false |  |
| CertHash | Specifies the hash of the License Server certificate needing verification. | false | false |  |
| Credentials | Specifies the username/password to be authenticated with the License Server. | false | false |  |
| AccountSid | Specifies the security identifier of the Active Directory account or group to be removed from the list of administrators for the License Server. | true | true (ByPropertyName) |  |

## Input Type

### 

## Return Values

### 

## Notes
If the command fails, one of the following errors is returned.<br>    Error Codes<br>    -----------<br>    LicensingAdminStatus.UserNotFound<br>        The specified Active Directory account or group could not be found.<br>    LicensingAdminStatus.UserNotAuthorized<br>        The currently authenticated user is not authorized to perform this operation.<br>    LicensingAdminStatus.CommunicationError<br>        There was a problem communicating with the License Server.<br>    LicensingAdminStatus.UnknownError<br>        An unexpected error occurred.  For more details, see the Windows event logs on the controller.
## Examples

### Example 1
```
C:\PS>Remove-LicAdministrator -AdminAddress https://licserver.mydomain.net:8083 -Account "mydomain\Domain Users"
```Removes administrator access to the License Server for all users in the domain named 'mydomain'.
### Example 2
```
C:\PS>Remove-LicAdministrator -AdminAddress https://licserver.mydomain.net:8083 -AccountSid S-1-5-21-1315084875-1285793635-2418178940-1201
```Removes administrator access to the License Server for the Active Directory account or group with the security identifier 'S-1-5-21-1315084875-1285793635-2418178940-1201'.
