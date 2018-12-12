
# Test-Userprofileshare
Tests a prospective user profile store path for its suitability for use with Citrix Profile Management.
## Syntax
```
Test-UserProfileShare -PathSyntaxOnly -Path <String> [-Mandatory] [-RedirectedFolders] [<CommonParameters>]

Test-UserProfileShare -Path <String> -UserGroups <String[]> -AdminGroups <String[]> [-Mandatory] [-RedirectedFolders] [<CommonParameters>]

Test-UserProfileShare -Path <String> -UserGroupsSids <String[]> -AdminGroupsSids <String[]> [-Mandatory] [-RedirectedFolders] [<CommonParameters>]
```
## Detailed Description
This command can be used as a validation step prior to configuring the profile store path in a production environment, in order to gain confidence that the profile manager and the store will function together correctly.

This command runs a sequence of tests on the nominated path, and reports the results via the output pipeline. The tests are organised into two distinct phases. The first phase examines the syntax of the supplied store path string. The second phase examines the profile store itself, checking that the required network shares exist, and that their permissions are appropriately configured according to best practices. If any faults are discovered with the syntax of the path string, these will be reported via the output pipeline, and the command will halt early without attempting to examine the profile store. The profile store will only be examined if the path is syntactically correct.

This command can be used in combination with the Repair-UserProfileShare cmdlet, which is able to automatically correct some of the problems that are found during inspection of the profile store. Problems with the syntax of the path can never be repaired. Syntactic issues must be fixed by the administrator re-typing the path and testing the store again.


## Related Commands

## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| PathSyntaxOnly | This switch indicates the the command should only check the syntax of the user store path. | true | false |  |
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
This cmdlet outputs a sequence of objects, each of which has the following properties:<br>Name - This property indicates the name of the test.<br>Status - This property indicates whether the test has passed or failed.<br>Details - This property provides additional information about the test in the case where it has failed. The interpretation of this property depends on the name of the test.<br>CanFix - In the case where the test has failed, this boolean property indicates whether the problem can be fixed with the Repair-UserProfileShare cmdlet.
## Examples

### Example 1
```
C:PS> Test-UserProfileShare -Path \\ProfileServer\Profiles$\%USERNAME%.%USERDOMAIN% -UserGroups @("FABRIKAM\Domain Users") -AdminGroups @("FABRIKAM\Administrators")
```
#### Description
This command tests that the path "\\\\ProfileServer\\Profiles\$\\%USERAME%.%USERDOMAIN%" is suitable for use as a profile store. This path is syntactically valid, so the cmdlet will check for the existence of the share "\\\\ProfileServer\\Profiles\$". Provided that the share exists, it will also check that its permissions are configured such that all domain users would be permitted to create profile folders within the store, and that all domain administrators will be permitted to access the store for administrative purposes.
### Example 2
```
C:PS> Test-UserProfileShare -Path \\ProfileServer\Profiles$\FinanceDept\FixedProfile -UserGroups @("FABRIKAM\Domain Users") -AdminGroups @("FABRIKAM\Administrators") -Mandatory
```
#### Description
This command tests that the path "\\\\ProfileServer\\Profiles\$\\FinanceDept\\FixedProfile" contains a valid Citrix mandatory profile. This path is syntactically valid, so the cmdlet will check that the share "\\\\ProfileServer\\Profiles\$" exists. If it exists, the cmdlet will go on to check that its permissions are configured such that all domain users would be permitted to read data from the profile, and that all domain administrators will be permitted to access the profile for administrative purposes.&lt;br&gt;Additional checks will be performed on the contents of the profile to ensure that there is nothing within the profile that might reveal details about the user who logged in to create it.
