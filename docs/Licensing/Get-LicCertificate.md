
# Get-Liccertificate
Gets the self-signed X509 certificate from the specified License Server.
## Syntax
```
Get-LicCertificate [-AdminAddress] <String> [<CommonParameters>]
```
## Detailed Description
Returns the self-signed X509 Certificate from the specified License Server.


## Related Commands

## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| AdminAddress | Specifies the Web Services for Licensing address of the License Server that the PowerShell Snap-in will connect to.  Retrieve this address with Get-LicLocation. | true | true (ByValue) |  |

## Input Type

### 

## Return Values

### X509certificate

## Notes
If the command fails, one of the following errors is returned.<br>    Error Codes<br>    -----------<br>    LicensingAdminStatus.CommunicationError<br>        There was a problem communicating with the License Server.<br>    LicensingAdminStatus.UnknownError<br>        An unexpected error occurred.  For more details, see the Windows event logs on the controller.
## Examples

### Example 1
```
C:\PS>Get-LicCertificate -AdminAddress https://licserver.mydomain.net:8083

           Handle Issuer                                                             Subject

           ------ ------                                                             -------

         44758616 CN=lictest-LICTEST-DC-CA, DC=lictest, DC=my, DC=mydomain, DC=net   CN=CITRIX-LSTLT435.lictest.mydomain.net
```Returns the X509 certificate
