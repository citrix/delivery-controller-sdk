# Add-AdminPermission

   Add permissions to the set of permissions of a role.

## Syntax
```
Add-AdminPermission [-InputObject] <Permission[]> -Role <String> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]

Add-AdminPermission [-Permission] <String[]> -Role <String> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
```

## Detailed Description
   Add extra permissions to the set of permissions that a role maps to.

Any administrator with a right including that role immediately gains the ability to use the operations of the new permissions.

Duplicate permissions do not produce an error, and permissions are skipped if the role already contains the permission (without error).

You cannot modify the permissions of built-in roles.

## Related Commands
  * [Remove-AdminPermission](Remove-AdminPermission/)
  * [Get-AdminPermission](Get-AdminPermission/)
  * [Get-AdminRole](Get-AdminRole/)
  * [Get-AdminPermissionGroup](Get-AdminPermissionGroup/)
  * [Test-AdminAccess](Test-AdminAccess/)
## Parameters

| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| InputObject | Specifies the permissions to add. | true | true (ByValue) |  |
| Permission | Specifies the list of permissions to add (by identifier). | true | true (ByPropertyName) |  |
| Role | Role name or identifier of the role to update. | true | false |  |
| LoggingId | Specifies the identifier of the high-level operation this cmdlet call forms a part of. Citrix Studio and Director typically create high-level operations. PowerShell scripts can also wrap a series of cmdlet calls in a high-level operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller the PowerShell snap-in will connect to. You can provide this as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type
### Citrix.DelegatedAdmin.Sdk.Permission
   You can pipe a list of permissions to be added into this command.
## Return Values
### None
   
## Examples

### EXAMPLE 1
```
C:\PS> Add-AdminPermission -Role MyRole -Permission Global_Read,Logging_Read
```
   Description<br>-----------<br>Add a couple of specific permissions to the 'MyRole' role.
### EXAMPLE 2
```
C:\PS> $list = Get-AdminRole "Delivery Administrator" | Select -Expand Permissions
C:\PS> Add-AdminPermission -Role MyRole -Permission $list
```
   Description<br>-----------<br>Add all of the permissions of the Delivery Administrator role to MyRole.
