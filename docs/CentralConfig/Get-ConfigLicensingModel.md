# Get-ConfigLicensingModel

   Lists the supported licensing models.

## Syntax
```
Get-ConfigLicensingModel -ProductCode <String> [-BearerToken <String>] [-AdminAddress <String>] [<CommonParameters>]
```

## Detailed Description
   

## Related Commands
  * [Get-ConfigProduct](Get-ConfigProduct.html)
  * [Get-ConfigSite](Get-ConfigSite.html)
  * [Set-ConfigSite](Set-ConfigSite.html)
  * [Import-ConfigFeatureTable](Import-ConfigFeatureTable.html)
## Parameters

| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| ProductCode | The product code | true | false |  |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller the PowerShell snap-in will connect to. You can provide this as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type
### 
   
## Return Values
### System.String
   The list of supported licensing models for the specified product code.## Notes
   The Get-ConfigProduct cmdlet lists the available product codes.<br>    The site object returned by the Get-ConfigSite cmdlet contains the currently configured product code.
## Examples

### EXAMPLE 1
```
C:\PS> Get-ConfigLicensingModel -ProductCode "XDT"
```
   Description<br>-----------<br>Retrieves the list of supported licensing models for product code "XDT".
