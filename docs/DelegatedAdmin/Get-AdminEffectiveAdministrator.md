# Get-AdminEffectiveAdministrator

   Retrieve the effective administrator objects for a user.

## Syntax
```
Get-AdminEffectiveAdministrator [-Name] <String> [-AdminAddress <String>] [<CommonParameters>]
```

## Detailed Description
   This command determines what groups the specified user belongs to and retrieves the matching administrator records. It includes the set of rights that would be granted to the user if he or she used the system.

As this command uses Active Directory to determine what groups the user has, the caller must have the ability to read this information from Active Directory.

Only enabled administrator records are returned.

## Related Commands
  * [Get-AdminAdministrator](Get-AdminAdministrator.html)
## Parameters

| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| Name | User name or SID of user to query | true | true (ByValue) |  |
| AdminAddress | Specifies the address of a XenDesktop controller the PowerShell snap-in will connect to. You can provide this as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type
### string
   User name or SID of user to query
## Return Values
### Citrix.DelegatedAdmin.Sdk.Administrator
   Administrator records matching the specified user
## Examples

### EXAMPLE 1
```
C:\PS> Get-AdminEffectiveAdministrator MYDOMAIN\testuser
```
   Description<br>-----------<br>Retrieve the administrator records matching user 'testuser'.
