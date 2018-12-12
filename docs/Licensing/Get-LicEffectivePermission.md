
# Get-Liceffectivepermission
Returns the effective permission level of the administrator account.
## Syntax
```
Get-LicEffectivePermission [-AdminAddress] <String> [-CertHash <String>] [-Credentials <PSCredential>] [<CommonParameters>]
```
## Detailed Description
Returns the effective permission level of the administrator account.  If credentials are not supplied, the server queries the currently logged-on.


## Related Commands

* [Get-LicLocation](./Get-LicLocation/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| AdminAddress | Specifies the Web Services for Licensing address of the License Server that the PowerShell Snap-in will connect to.  Retrieve this address with Get-LicLocation. | true | true (ByValue) |  |
| CertHash | Specifies the hash of the License Server certificate to be verified. | false | false |  |
| Credentials | Specifies the username/password to be authenticated with the License Server. | false | false |  |

## Input Type

### 

## Return Values

### Citrix.Licensing.Admin.Sdk.Wslserverinfo

## Notes
If the command fails, one of the following errors is returned.<br>    Error Codes<br>    -----------<br>    LicensingAdminStatus.UserNotAuthorized<br>        The currently authenticated user is not authorized to perform this operation.<br>    LicensingAdminStatus.CommunicationError<br>        There was a problem communicating with the License Server.<br>    LicensingAdminStatus.UnknownError<br>        An unexpected error occurred.  For more details, see the Windows event logs on the controller.
## Examples

### Example 1
```
C:\PS>Get-LicEffectivePermission -AdminAddress https://licserver.mydomain.net:8083

Permissions  : Full
```Gets the effective permissions of the user.
