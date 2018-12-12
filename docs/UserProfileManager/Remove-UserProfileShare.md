
# Remove-Userprofileshare
Removes a nominated network share.
## Syntax
```
Remove-UserProfileShare [-Path] <String> [<CommonParameters>]
```
## Detailed Description
This command might be used as part of a final tear-down procedure for a profile store that is no longer needed.

This command will not delete any folders or data from the server computer, nor will it alter any access permissions on the folder. It will only restore the shared folder into an unshared state.


## Related Commands

## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| Path | This string specifies the full UNC name of the network share to be removed. Since it is a UNC name, it will naturally specify both the name of the server computer and the name of the share to be removed. Consequently, no additional inputs are required. | true | true (ByValue) |  |

## Input Type

### None

## Return Values

### None

## Examples

### Example 1
```
C:PS> Remove-UserProfileShare -Path \\ProfileServer\Profiles$
```
#### Description
This command will unpublish the network share called "Profiles\$" on the computer called "ProfileServer". The contents of the folder itself will not be affected. Any required deletion of profile store contents must be performed manually by an appropriate administrator of the folder.
