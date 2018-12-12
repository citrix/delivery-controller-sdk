
# Get-Ctxappvapplication
Enumerates all published App-V applications for a given Management Server.
## Syntax
```
Get-CtxAppVApplication [-AppVManagementServer] <string> [<CommonParameters>]
```
## Detailed Description
Queries a given Management Server and fetches all published applications for that server. Applications that are published but have no user entitlements are not displayed by this cmdlet.


## Related Commands

## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| AppVManagementServer | Machine name of the App-V Management Server. | true | true (ByValue) |  |

## Input Type

### 

## Return Values

### Citrix.Virtapp.Studio.Powershellmanager.Appvserverapplication

## Examples

### Example 1
```
Get-CtxAppVApplication -AppVManagementServer "appv-mansrv"
```
#### Description
Displays all applications available from the Management Server "appv-mansrv".
