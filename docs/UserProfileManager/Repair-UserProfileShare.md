
# Repair-Userprofileshare
Carries out one or more remedial actions on a profile store.
## Syntax
```
Repair-UserProfileShare -Path <String> [-Mandatory] [-RedirectedFolders] [<CommonParameters>]

Repair-UserProfileShare -Path <String> -UserGroups <String[]> -AdminGroups <String[]> [-Mandatory] [-RedirectedFolders] [<CommonParameters>]

Repair-UserProfileShare -Path <String> -UserGroupsSids <String[]> -AdminGroupsSids <String[]> [-Mandatory] [-RedirectedFolders] [<CommonParameters>]
```
## Detailed Description
Use this command in situations where the Test-UserProfileShare cmdlet reported one or more fixable faults with the profile store.

The inputs and outputs of this command are identical to those of Test-UserProfileShare. The only difference between the two cmdlets is that this cmdlet will attempt to fix the issues, where Test-UserProfileShare will only report them.

Issues that cannot be fixed will be reported as test failures, just as they would with Test-UserProfileShare.

This cmdlet can only be used to fix issues that were claimed to be fixable in the output report from Test-UserProfileShare.


## Related Commands

## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| Path | This string contains the prospective profile store path to be examined, such as "\\\\ProfileServer\\Profiles\$\\%USERNAME%.%USERDOMAIN%". | true | true (ByValue) |  |
| UserGroups | This array of strings specifies the names of security groups whose members will be creating their profiles in the store. This array must contain at least one entry. Each string must be specified as a Windows object identifier, such as "FABRIKAM\\Domain Users". | true | false |  |
| AdminGroups | This array of strings specifies the names of security groups that should be given an administrative level of access to the profile share. If no such access is required, the array can be supplied as empty. Each string must be specified as a Windows object identifier, such as "FABRIKAM\\Administrators". | true | false |  |
| UserGroupsSids | This array of strings specifies the SID of security groups whose members will be creating their profiles in the store. This array must contain at least one entry. Each string must be specified as security identifier string, such as "S-1-1-0". | true | false |  |
| AdminGroupsSids | This array of strings specifies the SID of security groups that should be given an administrative level of access to the profile share. If no such access is required, the array can be supplied as empty. Each string must be specified as security identifier string, such as "S-1-5-32-544". | true | false |  |
| Mandatory | This switch indicates whether the profile store is intended to house a mandatory profiles. Mandatory profile stores are subjected to additional checks. | false | false |  |
| RedirectedFolders | This switch indicates whether the path indicates the location of redirected folder directories. | false | false |  |

## Input Type

### None

## Return Values

### System.Management.Automation.Psobject
This cmdlet outputs a sequence of objects, each of which has the following properties:<br>Name - This property indicates the name of the test.<br>Status - This property indicates whether the repair action succeeded or failed.<br>Details - This property provides additional information about the test in the case where it has failed. The interpretation of this property depends on the name of the test.<br>CanFix - In the case where the test has failed, this boolean property indicates whether the problem can be fixed with the Repair-UserProfileShare cmdlet.
## Examples

### Example 1
```
C:PS> Repair-UserProfileShare -Path \\ProfileServer\Profiles$\%USERNAME%.%USERDOMAIN% -UserGroups @("FABRIKAM\Domain Users") -AdminGroups @("FABRIKAM\Administrators")
```
#### Description
This command ensures that the path "\\\\ProfileServer\\Profiles\$\\%USERAME%.%USERDOMAIN%" is suitable for use as a profile store. This path is syntactically valid, so the cmdlet will check for the existence of the share "\\\\ProfileServer\\Profiles\$". Provided that the share exists, it will also ensure that its permissions are configured such that all domain users would be permitted to create profile folders within the store, and that all domain administrators will be permitted to access the store for administrative purposes.
### Example 2
```
C:PS> Repair-UserProfileShare -Path \\ProfileServer\Profiles$\FinanceDept\FixedProfile -UserGroups @("FABRIKAM\Domain Users") -AdminGroups @("FABRIKAM\Administrators") -Mandatory
```
#### Description
This command ensures that the path "\\\\ProfileServer\\Profiles\$\\FinanceDept\\FixedProfile" contains a valid Citrix mandatory profile. This path is syntactically valid, so the cmdlet will check that the share "\\\\ProfileServer\\Profiles\$" exists. If it exists, the cmdlet will go on to ensure that its permissions are configured such that all domain users would be permitted to read data from the profile, and that all domain administrators will be permitted to access the profile for administrative purposes.&lt;br&gt;Additional repair actions will be performed on the contents of the profile to ensure that there is nothing within the profile that might reveal details about the user who logged in to create it.
