
# Get-Liclaclocation
Gets the License Administration Console (LAC) URL
## Syntax
```
Get-LicLACLocation [[-LicenseServerAddress] <String>] [[-LicenseServerPort] <Int32>] [<CommonParameters>]
```
## Detailed Description
Returns the complete URL for the License Administration Console


## Related Commands

## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| LicenseServerAddress | Specifies the address of the License Server that the PowerShell Snap-in will connect to.  This can be provided as a host name or an IP address. | false | false | LocalHost. |
| LicenseServerPort | License Server port number | false | false | 27000 |

## Input Type

### 

## Return Values

### String

## Notes
If the command fails, one of the following errors is returned.<br>    Error Codes<br>    -----------<br>    LicensingAdminStatus.CommunicationError<br>        There was a problem communicating with the License Server.<br>    LicensingAdminStatus.UnknownError<br>        An unexpected error occurred.  For more details, see the Windows event logs on the controller.
## Examples

### Example 1
```
C:\PS>Get-LicLACLocation -LicenseServerAddress licserver.mydomain.net

https://licserver.mydomain.net:8082/
```Returns the address of the Licensing Administration Console on the specified server.
