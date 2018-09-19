# Get-ConfigProductFeature

   Lists the supported features.

## Syntax
```
Get-ConfigProductFeature [-ProductCode] <String> [-AdminAddress <String>] [<CommonParameters>]
```

## Detailed Description
   Lists the supported features. Use the Get-ConfigEnabledFeature command to determine which features are currently enabled.

## Related Commands
  * [Get-ConfigProduct](Get-ConfigProduct/)
  * [Get-ConfigSite](Get-ConfigSite/)
  * [Set-ConfigSite](Set-ConfigSite/)
  * [Import-ConfigFeatureTable](Import-ConfigFeatureTable/)
## Parameters

| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| ProductCode | The product code | true | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller the PowerShell snap-in will connect to. You can provide this as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type
### 
   
## Return Values
### System.String
   The list of supported licensing models for the specified product code.## Notes
   The Get-ConfigProduct cmdlet lists the available product codes.<br>    The site object returned by Get-ConfigSite cmdlet contains the currently configured product code.
## Examples

### EXAMPLE 1
```
C:\PS> Get-ConfigProductFeature -ProductCode "XDS"
```
   Description<br>-----------<br>Retrieves the list of supported features for XenDesktop.
