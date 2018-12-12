# Get-ConfigZone

   Gets zones configured for this site.

## Syntax
```
Get-ConfigZone [[-Name] <String>] [-Uid <Guid>] [-ControllerName <String>] [-ControllerSid <String>] [-Description <String>] [-ExternalUid <Guid>] [-IsPrimary <Boolean>] [-Metadata <String>] [-TenantId <Guid>] [-Property <String[]>] [-ReturnTotalRecordCount] [-MaxRecordCount <Int32>] [-Skip <Int32>] [-SortBy <String>] [-Filter <String>] [-BearerToken <String>] [-AdminAddress <String>] [<CommonParameters>]
```

## Detailed Description
   Retrieves zones matching the specified criteria. If no parameters are specified all zones will be returned.

## Related Commands
  * [New-ConfigZone](New-ConfigZone.html)
  * [Set-ConfigZone](Set-ConfigZone.html)
  * [Rename-ConfigZone](Rename-ConfigZone.html)
  * [Remove-ConfigZone](Remove-ConfigZone.html)
  * [Set-ConfigSite](Set-ConfigSite.html)
  * [Set-ConfigService](Set-ConfigService.html)
## Parameters

| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| Name | Gets zones with the specified name. | false | true (ByValue, ByPropertyName) |  |
| Uid | Gets the zone with the specified UID. | false | true (ByPropertyName) |  |
| ControllerName | Gets the zone that contains a specified Controller identified by Name. | false | false |  |
| ControllerSid | Gets the zone that contains a specified Controller identified by SID. | false | false |  |
| Description | Gets zones with the specified description. | false | false |  |
| ExternalUid | Specifies the ExternalUid of the zone. This is used for cloud sites to link with the Citrix Resource Location. | false | false |  |
| IsPrimary | Gets zones with the specified value of the IsPrimary flag. If true, only the primary zone may be returned; if false, all other zones may be returned. | false | false |  |
| Metadata | Gets records with matching metadata entries.<br>The value being compared with is a concatenation of the key name, a colon, and the value. For example: -Metadata "abc:x*" matches records with a metadata entry having a key name of "abc" and a value starting with the letter "x". | false | false |  |
| TenantId | Gets the zones associated with the specified Tenant ID | false | false |  |
| Property | Specifies the properties to be returned. This is similar to piping the output of the command through Select-Object, but the properties are filtered more efficiently at the server. | false | false |  |
| ReturnTotalRecordCount | When specified, the cmdlet outputs an error record containing the number of records available. This error record is additional information and does not affect the objects written to the output pipeline. See about_Config_Filtering for details. | false | false | False |
| MaxRecordCount | Specifies the maximum number of records to return. | false | false | 250 |
| Skip | Skips the specified number of records before returning results. Also reduces the count returned by -ReturnTotalRecordCount. | false | false | 0 |
| SortBy | Sorts the results by the specified list of properties. The list is a set of property names separated by commas, semi-colons, or spaces. Optionally, prefix each name with a + or - to indicate ascending or descending order. Ascending order is assumed if no prefix is present. | false | false | The default sort order is by name or unique identifier. |
| Filter | Gets records that match a PowerShell-style filter expression. See about_Config_Filtering for details. | false | false |  |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller the PowerShell snap-in will connect to. You can provide this as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type
### None
   You cannot pipe input into this cmdlet.
## Return Values
### Citrix.Configuration.Sdk.Zone
   Get-ConfigZone returns an object for each matching zone.
## Examples

### EXAMPLE 1
```
C:\PS> Get-ConfigZone -Name "London"
```
   Description<br>-----------<br>Gets the details of the zone with the specific name.
### EXAMPLE 2
```
C:\PS> Get-ConfigZone -IsPrimary $false
```
   Description<br>-----------<br>Lists all non-primary zones.
