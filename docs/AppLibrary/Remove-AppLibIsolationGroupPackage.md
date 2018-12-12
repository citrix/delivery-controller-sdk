﻿
# Remove-Applibisolationgrouppackage
Removes an AppV package from an isolation group
## Syntax
```
Remove-AppLibIsolationGroupPackage [-IsolationGroupUid] <Int32> -AppVPackageUid <Int32> [-LoggingId <Guid>] [-BearerToken <String>] [-AdminAddress <String>] [<CommonParameters>]
```
## Detailed Description
Removes the App-V package with the unique identifier in the specified isolation group


## Related Commands

## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| IsolationGroupUid | The isolation group's internal unique identifier. | true | true (ByValue, ByPropertyName) |  |
| AppVPackageUid | The unique identifier of the package within the isolation group. | true | true (ByPropertyName) |  |
| LoggingId | Specifies the identifier of the high-level operation this cmdlet call forms a part of. Citrix Studio and Director typically create high-level operations. PowerShell scripts can also wrap a series of cmdlet calls in a high-level operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller the PowerShell snap-in will connect to. You can provide this as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type

### 

## Return Values

### None

## Examples

### Example 1
```
Remove-AppLibIsolationGroupPackage -IsolationGroupUid 4 -AppVPackageUid 15
```
#### Description
Removes the App-V package with the unique identifier in the specified isolation group.
