# Get-AdminEffectiveRight

   Gets the set of Right objects associated with the current user.

## Syntax
```
Get-AdminEffectiveRight [-AdminAddress <String>] [<CommonParameters>]
```

## Detailed Description
   The Get-AdminEffectiveRight cmdlet returns the effective rights of the current user. This is the union of all rights of the enabled administrators that the current user matches, taking into account Active Directory group membership.

## Related Commands
  * [Get-AdminAdministrator](Get-AdminAdministrator/)
  * [Add-AdminRight](Add-AdminRight/)
  * [Remove-AdminRight](Remove-AdminRight/)
## Parameters

| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| AdminAddress | Specifies the address of a XenDesktop controller the PowerShell snap-in will connect to. You can provide this as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type
### None
   You cannot pipe input into this cmdlet.
## Return Values
### Citrix.DelegatedAdmin.Sdk.Right
   The Rights associated with the current user
## Examples

### EXAMPLE 1
```
C:\PS> Get-AdminEffectiveRight
```
   Description<br>-----------<br>Return the effective rights for the current user.
