# Set-AdminAdministrator

   Sets the properties of an administrator.

## Syntax
```
Set-AdminAdministrator [-InputObject] <Administrator[]> [-Enabled <Boolean>] [-PassThru] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]

Set-AdminAdministrator -Sid <String[]> [-Enabled <Boolean>] [-PassThru] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]

Set-AdminAdministrator [-Name] <String[]> [-Enabled <Boolean>] [-PassThru] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
```

## Detailed Description
   The Set-AdminAdministrator cmdlet is used to enable or disable an existing administrator.

You can specify the administrators to modify in a number of ways, by piping in existing objects, by passing existing objects with the InputObject parameter, or by specifying the names or SIDs explicitly.

## Related Commands
  * [New-AdminAdministrator](New-AdminAdministrator.html)
  * [Get-AdminAdministrator](Get-AdminAdministrator.html)
  * [Remove-AdminAdministrator](Remove-AdminAdministrator.html)
  * [Set-AdminAdministratorMetadata](Set-AdminAdministratorMetadata.html)
  * [Remove-AdminAdministratorMetadata](Remove-AdminAdministratorMetadata.html)
## Parameters

| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| InputObject | Specifies the administrators to modify. | true | true (ByValue) |  |
| Name | Specifies the names of the administrators to modify. | true | true (ByPropertyName) |  |
| Sid | Specifies the SIDs of the administrators to modify. | true | true (ByPropertyName) |  |
| Enabled | Specifies the new value for the Enabled property. | false | false |  |
| PassThru | Returns the affected record. By default, this cmdlet does not generate any output. | false | false | False |
| LoggingId | Specifies the identifier of the high-level operation this cmdlet call forms a part of. Citrix Studio and Director typically create high-level operations. PowerShell scripts can also wrap a series of cmdlet calls in a high-level operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller the PowerShell snap-in will connect to. You can provide this as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type
### Citrix.DelegatedAdmin.Sdk.Administrator
   You can pipe the adminstrators to be modified into this command.
## Return Values
### None or Citrix.DelegatedAdmin.Sdk.Administrator
   When you use the PassThru parameter, Set-AdminAdministrator generates a Citrix.DelegatedAdmin.Sdk.Administrator object. Otherwise, this cmdlet does not generate any output.
## Examples

### EXAMPLE 1
```
C:\PS> Get-AdminAdministrator -Enabled $false | Set-AdminAdministrator -Enabled $true
```
   Description<br>-----------<br>Enable all administrators that are currently disabled.
### EXAMPLE 2
```
C:\PS> Set-AdminAdministrator -Name DOMAIN\TestUser1,DOMAIN\TestUser2 -Enabled $true
```
   Description<br>-----------<br>Enable two specific users specified by name (TestUser1 and TestUser2).
