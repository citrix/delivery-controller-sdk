
# Get-Liclocation
Gets the location of the specified License Server service
## Syntax
```
Get-LicLocation [[-LicenseServerAddress] <String>] [[-LicenseServerPort] <Int32>] [[-AddressType] <String>] [<CommonParameters>]
```
## Detailed Description
Returns the complete URL (or address:port) for the License Server service


## Related Commands

## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| LicenseServerAddress | Specifies the address of the License Server that the PowerShell Snap-in will connect to.  You can provide it as a host name or an IP address. | false | false | LocalHost. |
| LicenseServerPort | License Server port number | false | false | 27000 |
| AddressType | Address type of the License Service \[LS|VD|LAC|WSL\] | false | false | WSL |

## Input Type

### 

## Return Values

### String

## Notes
If the command fails, one of the following errors is returned.<br>    Error Codes<br>    -----------<br>    LicensingAdminStatus.InvalidType<br>        The AddressType specified was not one of the supported types (LS|VD|LAC|WSL).<br>    LicensingAdminStatus.CommunicationError<br>        There was a problem communicating with the License Server.<br>    LicensingAdminStatus.UnknownError<br>        An unexpected error occurred.  For more details, see the Windows event logs on the controller.
## Examples

### Example 1
```
C:\PS>Get-LicLocation -LicenseServerAddress licserver.mydomain.net -LicenseServerPort 27001 -AddressType WSL

https://licserver.mydomain.net:8083/
```Returns the address of the Web Services for Licensing (WSL) service on the specified server.
