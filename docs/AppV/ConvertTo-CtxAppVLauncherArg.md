
# Convertto-Ctxappvlauncherarg
Returns a string containing information to send to the App-V Launcher. You can plug this string directly into the Virtual Delivery Agent (VDA) to launch App-V applications.
## Syntax
```
ConvertTo-CtxAppVLauncherArg [-AppVPublishingServer] <string> [-AppId] <String> [[-PackageId] <String>] -SeqLoc <String> -TargetInPackage <boolean> [<CommonParameters>]

ConvertTo-CtxAppVLauncherArg [-LauncherPath] <SwitchParameter> [<CommonParameters>]
```
## Detailed Description
Returns a string containing information to send to the App-V Launcher. You can plug this string directly into the Virtual Delivery Agent (VDA) to launch App-V applications.


## Related Commands

## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| AppVPublishingServer | The Url including the port number, of the publishing Server which is serving the application. | true | true (ByValue, ByPropertyName) |  |
| AppId | The AppId of the specific application for which CtxAppVLauncher argugents is required. | True | false |  |
| PackageId | The PackageId of the package to which the application belongs. | false | true (ByValue, ByPropertyName) |  |
| SeqLoc | The sequence location of the package. | true | false |  |
| TargetInPackage | Pass this as \$true if TargetInPackage field is "true" in the Manifest file for the particular App Id. | true | false |  |
| LauncherPath | Gets the Citrix Launcher path. The Citrix Launcher is a component installed on the VDA. | true | true (ByValue, ByPropertyName) |  |

## Input Type

### 

## Return Values

### 

## Examples

### Example 1
```
ConvertTo-CtxAppVLauncherArg -AppVPublishingServer "http://appv-pubsrv.mydomain.com:8082" -PackageId "1bcb6993-10b1-4659-b9d4-e809e10cecdf_5" -AppId "[{ProgramFilesX86}]\Beyond Compare 3\BCompare.exe" -SeqLoc "\\10.105.32.199\share\App-V\Firefox.appv" -TargetInPackage $true
```
#### Description
Converts the arguments provided into a cmdlet to launch Beyond Compare from the appv-pubsrv Publishing Server on the VDA.
### Example 2
```
ConvertTo-CtxAppVLauncherArg -LauncherPath
```
#### Description
Gets the Citrix App-V Launcher path.
