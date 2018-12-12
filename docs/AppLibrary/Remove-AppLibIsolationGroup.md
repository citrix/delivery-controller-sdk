﻿
# Remove-Applibisolationgroup
Removes an isolation group from the library
## Syntax
```
Remove-AppLibIsolationGroup [-IsolationGroupUid] <Int32> [-LoggingId <Guid>] [-BearerToken <String>] [-AdminAddress <String>] [<CommonParameters>]
```
## Detailed Description
The isolation group will be removed from the library that is holding it


## Related Commands

## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| IsolationGroupUid | The isolation group's internal unique identifier. | true | true (ByValue, ByPropertyName) |  |
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
Remove-AppLibIsolationGroup -Uid 5 -LibraryUid 1
```
#### Description
Removes the specified isolation group from the application library that holds it.
