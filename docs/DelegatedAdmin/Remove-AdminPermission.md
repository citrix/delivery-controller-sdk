# Remove-AdminPermission

   Remove permissions from the set of permissions of a role.

## Syntax
```
Remove-AdminPermission [-InputObject] <Permission[]> -Role <String> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]

Remove-AdminPermission [-Permission] <String[]> -Role <String> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]

Remove-AdminPermission -All -Role <String> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
```

## Detailed Description
   Remove permissions from the set of permissions that a role maps to.

Any administrator with a right including that role immediately loses the ability to use the operations of the removed permissions.

Duplicate permissions do not produce an error, and permissions that the roles does not already have are skipped (without error).

You cannot modify the permissions of built-in roles.

## Related Commands
  * [Add-AdminPermission](Add-AdminPermission/)
  * [Get-AdminPermission](Get-AdminPermission/)
  * [Get-AdminRole](Get-AdminRole/)
  * [Get-AdminPermissionGroup](Get-AdminPermissionGroup/)
  * [Test-AdminAccess](Test-AdminAccess/)
## Parameters

| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| InputObject | Specifies the permissions to remove. | true | true (ByValue) |  |
| Permission | Specifies the list of permissions to remove (by identifier). | true | true (ByPropertyName) |  |
| Role | Role name or identifier of the role to update. | true | false |  |
| All | Remove all permissions. | true | false |  |
| LoggingId | Specifies the identifier of the high-level operation this cmdlet call forms a part of. Citrix Studio and Director typically create high-level operations. PowerShell scripts can also wrap a series of cmdlet calls in a high-level operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller the PowerShell snap-in will connect to. You can provide this as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type
### Citrix.DelegatedAdmin.Sdk.Permission
   You can pipe a list of permissions to be removed into this command.
## Return Values
### None
   
## Examples

### EXAMPLE 1
```
C:\PS> Remove-AdminPermission -Role MyRole -Permission Global_Read,Logging_Read
```
   Description<br>-----------<br>Remove a couple of specific permissions from the 'MyRole' role.
### EXAMPLE 2
```
C:\PS> Remove-AdminPermission -Role MyRole -All
```
   Description<br>-----------<br>Remove all permissions from the 'MyRole' role.
