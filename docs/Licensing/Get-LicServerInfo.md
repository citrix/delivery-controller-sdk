
# Get-Licserverinfo
Returns information about the specified License Server.
## Syntax
```
Get-LicServerInfo [-AdminAddress] <String> [<CommonParameters>]
```
## Detailed Description
Returns server version and configuration information from the specified License Server.


## Related Commands

* [Get-LicLocation](./Get-LicLocation/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| AdminAddress | Specifies the Web Services for Licensing address of the License Server that the PowerShell Snap-in will connect to.  Retrieve this address with Get-LicLocation. | true | true (ByValue) |  |

## Input Type

### 

## Return Values

### Citrix.Licensing.Admin.Sdk.Wslserverinfo

## Notes
If the command fails, one of the following errors is returned.<br>    Error Codes<br>    -----------<br>    LicensingAdminStatus.CommunicationError<br>        There was a problem communicating with the License Server.<br>    LicensingAdminStatus.UnknownError<br>        An unexpected error occurred.  For more details, see the Windows event logs on the controller.
## Examples

### Example 1
```
C:\PS>Get-LicServerInfo -AdminAddress https://licserver.mydomain.net:8083

WSLVersion   : 2.0

SLVersion    : v11.11.0.0 build 106800 i86_n3

Locale       : en

HostName     : mainls.xd.local

HostIP       : 10.8.6.189

HostName     : Admin11

UserDomain   : PV2WM

Permissions  : Full
```Gets the version, host and user information from the specified License Server.
