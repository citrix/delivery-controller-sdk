﻿# New-ConfigZone

   Creates a new zone in the site.

## Syntax
```
New-ConfigZone [-Name] <String> [-Description <String>] [-ExternalUid <Guid>] [-TenantId <Guid>] [-LoggingId <Guid>] [-BearerToken <String>] [-AdminAddress <String>] [<CommonParameters>]
```

## Detailed Description
   Creates a new zone in the site.

A Zone represents a subset of the site infrastructure residing in a particular geographical location.

By default any new zone will be marked as secondary. To specify the primary zone use the Set-ConfigSite cmdlet.

To associate controllers with a zone use the Set-ConfigService cmdlet.

## Related Commands
  * [Get-ConfigZone](Get-ConfigZone.html)
  * [Set-ConfigSite](Set-ConfigSite.html)
  * [Set-ConfigService](Set-ConfigService.html)
  * [Set-ConfigZone](Set-ConfigZone.html)
  * [Rename-ConfigZone](Rename-ConfigZone.html)
  * [Remove-ConfigZone](Remove-ConfigZone.html)
## Parameters

| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| Name | Specifies the name of the zone. Each zone in a site must have a unique name. | true | true (ByPropertyName) |  |
| Description | Specifies the description of the zone. | false | true (ByPropertyName) |  |
| ExternalUid | Specifies the ExternalUid of the zone. This is used for cloud sites to link with the Citrix Resource Location. | false | true (ByPropertyName) |  |
| TenantId | Specifies the Tenant ID that the zone is associated with. This is used for cloud sites to associate zones with particular customers. | false | true (ByPropertyName) |  |
| LoggingId | Specifies the identifier of the high-level operation this cmdlet call forms a part of. Citrix Studio and Director typically create high-level operations. PowerShell scripts can also wrap a series of cmdlet calls in a high-level operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller the PowerShell snap-in will connect to. You can provide this as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type
### None
   You cannot pipe input into this cmdlet.
## Return Values
### Citrix.Configuration.Sdk.Zone
   The newly created zone.
## Examples

### EXAMPLE 1
```
C:\PS> $zone = New-ConfigZone -Name "London" -Description "London branch office"
C:\PS> Set-ConfigSite -PrimaryZone $zone
C:\PS> Set-ConfigService -Service "S-1-5-21-3384143951-2794580461-1950386216-8227" -Zone $zone
```
   Description<br>-----------<br>Creates a new zone called 'London', marks it as the primary zone and moves a controller to that zone.
