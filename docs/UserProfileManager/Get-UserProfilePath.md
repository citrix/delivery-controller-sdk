
# Get-Userprofilepath
Gets the path (or paths) at which an individual user's profile is stored.
## Syntax
```
Get-UserProfilePath -User <String> -PathToUserStore <String> [<CommonParameters>]
```
## Detailed Description
Use this cmdlet to search for specific user profile folders, based on a configured store path.

The cmdlet will perform automatic substitutions on all of the dynamic parts of the store path. These substitutions will be made based either on the details of the individual user given, or by enumerating all possible strings that are permitted by the variable in question. The approach taken depends on the variable. User-specific variables such as %USERNAME% will be substituted based on the user. Variables such as !CTX\_OSNAME! will be substituted by enumerating the possibilities.

Once all substitutions have been made, the cmdlet will search the user store for any directories that exist, matching the substituted path. All such directories are then reported as outputs of the cmdlet.

Once this cmdlet has been used to locate the profile store, other Windows PowerShell scripts can be written to inspect or manipulate the contents of the profile, provided that such access is allowed by the permissions of the profile store.


## Related Commands

## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| User | Specifies the user whose profile is to be found within the store. Users can be identified in terms of their account name, UPN or SID. | true | true (ByValue) |  |
| PathToUserStore | Specifies the UNC path to the configured profile store. | true | false |  |

## Input Type

### System.String
The pipeline accepts any valid User parameter, as an account name, UPN or SID.
## Return Values

### System.String
The UNC path to the profile folder(s) belonging to the specified user. Each reported path will denote a directory that exists within the store, and will have all of its dynamic elements substituted with static strings.
## Examples

### Example 1
```
c:\PS>Get-UserProfilePath -PathToUserStore \\server\Profiles$\%USERNAME%.%USERDOMAIN% -User FABRIKAM\Fred
```
#### Description
This command attempts to locate the user profile folder for the user account Fred within the domain FABRIKAM, where the user has been specified as an NT account name. This user's details will be substituted into the profile store path. A likely return result would be \\\\server\\Profiles\$\\Fred.FABRIKAM.
### Example 2
```
c:\PS>Get-UserProfilePath -PathToUserStore \\server\Profiles$\%USERNAME%.%USERDOMAIN%\!CTX_OSNAME! -User Fred@FABRIKAM
```
#### Description
This command attempts to locate the user profile folder for the user account Fred within the domain FABRIKAM, where the user has been specified as a User Principal Name (UPN). This user's details will be substituted into the profile store path. Possible return results might be \\\\server\\Profiles\$\\Fred.FABRIKAM\\Win7 or \\\\server\\Profiles\$\\Fred.FABRIKAM\\WinXP.
### Example 3
```
c:\PS>Get-UserProfilePath -PathToUserStore \\server\Profiles$\%USERNAME%.%USERDOMAIN%\!CTX_OSBITNESS! -User S-1-5-32-1045337234-12924708993-5683276719-19000
```
#### Description
This command attempts to locate the user profile folder for the user account whose Security Identifier (SID) has been specified. This user's details will be substituted into the profile store path. Possible return results might be \\\\server\\Profiles\$\\Fred.FABRIKAM\\x86 or \\\\server\\Profiles\$\\Fred.FABRIKAM\\x64.
