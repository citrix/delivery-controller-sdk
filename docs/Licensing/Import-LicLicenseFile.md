
# Import-Liclicensefile
Import License File to the License Server
## Syntax
```
Import-LicLicenseFile [-AdminAddress] <String> -FileName <String> [-Overwrite] [-CertHash <String>] [-Credentials <PSCredential>] [<CommonParameters>]
```
## Detailed Description
Imports the file specified in the Filename parameter to the specified License Server, with an optional parameter to overwrite an existing file.


## Related Commands

## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| AdminAddress | Specifies the Web Services for Licensing address of the License Server that the PowerShell Snap-in will connect to.  Retrieve this address with Get-LicLocation. | true | true (ByValue) |  |
| FileName | Full Path to the Location of the License File.  The Filename will be the same on the License Server. | true | false |  |
| Overwrite | Switch to specify whether or not to overwrite an existing file with the same filename. | false | false | false |
| CertHash | Specifies the hash of the License Server certificate needing verification. | false | false |  |
| Credentials | Specifies the username/password to be authenticated with the License Server. | false | false |  |

## Input Type

### 

## Return Values

### 

## Notes
If the command fails, one of the following errors is returned.<br>    Error Codes<br>    -----------<br>    LicensingAdminStatus.Success<br>        Succesfully Imported the File to License Server<br>    LicensingAdminStatus.FileAlreadyExists<br>        License File Already Exists, use Overwrite flag<br>    LicensingAdminStatus.FileWriteFailed<br>        Failed to write the license file<br>    LicensingAdminStatus.FileOpenFailed<br>        Failed to open file for writing<br>    LicensingAdminStatus.InvalidLicenseFile<br>        License File Begin Imported is not a Valid License File<br>    LicensingAdminStatus.FileNotFound<br>        File Being Imported Does not Exist<br>    LicensingAdminStatus.UnknownError<br>        An unexpected error occurred.  For more details, see the Windows event logs on the controller.
## Examples

### Example 1
```
C:\PS>Import-LicLicenseFile -AdminAddress https://licserver.mydomain.net:8083 -FileName "C:\Demo.lic" -Overwrite
```Imports the license file on the License Server and overwrites the license Demo.lic if already present.
