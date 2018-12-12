# Remove-ConfigZone

   Removes a zone from the site.

## Syntax
```
Remove-ConfigZone [-InputObject] <Zone[]> [-LoggingId <Guid>] [-BearerToken <String>] [-AdminAddress <String>] [<CommonParameters>]

Remove-ConfigZone [-Uid] <Guid[]> [-LoggingId <Guid>] [-BearerToken <String>] [-AdminAddress <String>] [<CommonParameters>]

Remove-ConfigZone [-Name] <String[]> [-LoggingId <Guid>] [-BearerToken <String>] [-AdminAddress <String>] [<CommonParameters>]
```

## Detailed Description
   This cmdlet removes zones from a site.

You cannot remove a zone that is marked as primary or has associated controllers.

## Related Commands
  * [Get-ConfigZone](Get-ConfigZone.html)
  * [New-ConfigZone](New-ConfigZone.html)
  * [Set-ConfigZone](Set-ConfigZone.html)
  * [Rename-ConfigZone](Rename-ConfigZone.html)
  * [Set-ConfigSite](Set-ConfigSite.html)
  * [Set-ConfigService](Set-ConfigService.html)
## Parameters

| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| InputObject | Specifies the zone to remove (by zone object). | true | true (ByValue) |  |
| Uid | Specifies the zone to remove (by Uid). | true | true (ByPropertyName) |  |
| Name | Specifies the zone to remove (by Name). | true | true (ByPropertyName) |  |
| LoggingId | Specifies the identifier of the high-level operation this cmdlet call forms a part of. Citrix Studio and Director typically create high-level operations. PowerShell scripts can also wrap a series of cmdlet calls in a high-level operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller the PowerShell snap-in will connect to. You can provide this as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type
### Citrix.Configuration.Sdk.Zone
   You can pipe the zones to be deleted into this command.
## Return Values
### None
   
## Examples

### EXAMPLE 1
```
C:\PS> Remove-ConfigZone -Name 'Sydney'
```
   Description<br>-----------<br>Remove the zone specified by name. This fails if one of the zones has controllers associated.
### EXAMPLE 2
```
C:\PS> Get-ConfigService | Set-ConfigService -Zone (Get-ConfigZone -IsPrimary $true)
C:\PS> Get-ConfigZone -IsPrimary $false | Remove-ConfigZone
```
   Description<br>-----------<br>Move all controllers to the primary zone. Remove all non-primary zones.
