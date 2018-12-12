
# New-Userprofileshare
Creates a new Windows network share on a nominated computer, making it suitable for use as a profile store.
## Syntax
```
New-UserProfileShare -ServerName <String> -ShareName <String> -PathOnServer <String> -UserGroups <String[]> -AdminGroups <String[]> [<CommonParameters>]
```
## Detailed Description
Use this command as part of the procedure for creating a new profile store when configuring profile management for first use. A suitable folder is assumed to already exist locally on the nominated computer. If no such folder exists, then you will need to create it on the machine before running this command. This command automates the process of transforming that folder into a published network share with suitable access control for profile management.

When using this command to publish a share, you will need to supply information about the security groups of users who will be storing their profiles on the share. You can also optionally specify security groups who will be given an administrative level of access, should your organisation require this.


## Related Commands

## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| ServerName | This string specifies the network identity of the computer on which the share is being published. | true | false |  |
| ShareName | This specifies the desired name of the share itself. It is recommended (although not required) that share names end with the "\$" character, so that they are excluded from casual enumerations of available shares. | true | false |  |
| PathOnServer | This string specifies the absolute path of the local directory on the server computer, which will become the shared folder. This path must make sense from the point of view of the server, so it must not be a UNC path. A path might, for example, be of the form "C:\\UserProfiles\\FinanceDepartment". | true | false |  |
| UserGroups | This array of strings specifies the names of security groups whose members will be creating their profiles in the store. This array must contain at least one entry. Each string must be specified as a Windows object identifier, such as "FABRIKAM\\Domain Users". | true | false |  |
| AdminGroups | This array of strings specifies the names of security groups that should be given an administrative level of access to the profile share. If no such access is required, the array can be supplied as empty. Each string must be specified as a Windows object identifier, such as "FABRIKAM\\Administrators". | true | false |  |

## Input Type

### None

## Return Values

### None

## Examples

### Example 1
```
C:PS> New-UserProfileShare -ServerName ProfileServer -ShareName Profiles$ -PathOnServer C:\ProfileStore -UserGroups @("FABRIKAM\Domain Users") -AdminGroups @("FABRIKAM\Administrators")
```
#### Description
This command creates a new network share called "Profiles\$" on the machine called "ProfileServer". It does this by sharing the folder "C:\\ProfileStore", which will already be resident on ProfileServer. The store can be used by all domain users in the FABRIKAM domains. The store (including all of the user profiles that are subsequently stored within it) will also be accessible to the domain administrators. Following successful execution of this command, the network share whose UNC name is "\\\\ProfileServer\\Profiles\$" will exist. This makes it possible, for instance, to establish "\\\\ProfileServer\\Profiles\$\\%USERNAME%.%USERDOMAIN" as a valid store path when configuring profile management.
