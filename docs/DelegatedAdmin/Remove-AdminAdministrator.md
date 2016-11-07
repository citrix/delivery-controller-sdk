# Remove-AdminAdministrator

   Removes administrators from the site.

## Syntax
```
Remove-AdminAdministrator [-InputObject] <Administrator[]> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]

Remove-AdminAdministrator -Sid <String[]> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]

Remove-AdminAdministrator [-Name] <String[]> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
```

## Detailed Description
   The Remove-AdminAdministrator cmdlet deletes administrators from the site.

## Related Commands
  * [New-AdminAdministrator](New-AdminAdministrator.html)
  * [Get-AdminAdministrator](Get-AdminAdministrator.html)
  * [Set-AdminAdministrator](Set-AdminAdministrator.html)
  * [Set-AdminAdministratorMetadata](Set-AdminAdministratorMetadata.html)
  * [Remove-AdminAdministratorMetadata](Remove-AdminAdministratorMetadata.html)
## Parameters

| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| InputObject | Specifies the administrators to delete. | true | true (ByValue) |  |
| Name | Specifies the name of the administrator to delete. | true | true (ByPropertyName) |  |
| Sid | Specifies the SID of the administrator to delete. | true | true (ByPropertyName) |  |
| LoggingId | Specifies the identifier of the high-level operation this cmdlet call forms a part of. Citrix Studio and Director typically create high-level operations. PowerShell scripts can also wrap a series of cmdlet calls in a high-level operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller the PowerShell snap-in will connect to. You can provide this as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type
### Citrix.DelegatedAdmin.Sdk.Administrator
   You can pipe the adminstrators to be deleted into this command.
## Return Values
### None
   
## Examples

### EXAMPLE 1
```
C:\PS> Remove-AdminAdministrator DOMAIN\TestUser
```
   Description<br>-----------<br>Remove the administrator called "DOMAIN\TestUser".
### EXAMPLE 2
```
C:\PS> Get-AdminAdministrator -Enabled $false | Remove-AdminAdministrator
```
   Description<br>-----------<br>Remove all disabled administrators.
