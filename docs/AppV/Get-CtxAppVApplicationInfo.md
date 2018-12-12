
# Get-Ctxappvapplicationinfo
Enumerates information for a given application in a given package for a given Management Server.
## Syntax
```
Get-CtxAppVApplicationInfo [-AppVManagementServer] <string> [-AppId] <String> [-PackageID] <string> [[-Property] <string[]>] [<CommonParameters>]

Get-CtxAppVApplicationInfo [-AppVManagementServer] <String> [[-InputObject] <AppVServerApplications[]>] [[-Property] <string[]>] [<CommonParameters>]
```
## Detailed Description
Queries a given Management Server and fetches the requested information for a given application.


## Related Commands

## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| AppvManagementServer | Machine name of the App-V Management Server. | true | true (ByValue) |  |
| AppId | The AppId of the specific application for which information is required. | false | false |  |
| PackageId | The PackageId of the package to which the application belongs. | false | false |  |
| InputObject | AppVServerApplication objects for which information is required. | false | false |  |
| Property | An array of the names of the property values to be pupulated in the returned data. | false | false |  |

## Input Type

### 

## Return Values

### Citrix.Virtapp.Studio.Powershellmanager.Appvappdata

## Examples

### Example 1
```
Get-CtxAppVApplicationInfo -AppVManagementServer "appv-mansrv" -AppId "[{ProgramFilesX86}]\Beyond Compare 3\BCompare.exe"  -PackageId "1bcb6993-10b1-4659-b9d4-e809e10cecdf_5"
```
#### Description
Fetches all application information for the 'Beyond Compare 3' application from the appv-mansrv Management Server.
### Example 2
```
Get-CtxAppVApplicationInfo -AppVManagementServer "appv-mansrv" -AppId "[{ProgramFilesX86}]\Beyond Compare 3\BCompare.exe"  -PackageId "1bcb6993-10b1-4659-b9d4-e809e10cecdf_5" -Property @('FTA','USERS')
```
#### Description
Fetches only information about FTA and user entitlements for the Beyond Compare 3 application from the appv-mansrv Management Server.
### Example 3
```
Get-CtxAppVApplication -AppVManagementServer "appv-mansrv" | Get-CtxAppVApplicationInfo -AppVManagementServer "appv-mansrv"
```
#### Description
Pipelines the output of Get-CtxAppvApplication to Get-CtxAppvApplicationInfo to get the application properties of all the published applications on the appv-mansrv Management Server.
