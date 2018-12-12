# Import-ConfigFeatureTable

   Sets the feature table of the site.

## Syntax
```
Import-ConfigFeatureTable [-Path] <String> [-LoggingId <Guid>] [-BearerToken <String>] [-AdminAddress <String>] [<CommonParameters>]

Import-ConfigFeatureTable -Content <String> [-LoggingId <Guid>] [-BearerToken <String>] [-AdminAddress <String>] [<CommonParameters>]
```

## Detailed Description
   

## Related Commands
  * [Export-ConfigFeatureTable](Export-ConfigFeatureTable.html)
  * [Get-ConfigSite](Get-ConfigSite.html)
  * [Set-ConfigSite](Set-ConfigSite.html)
  * [Get-ConfigProduct](Get-ConfigProduct.html)
  * [Get-ConfigProductEdition](Get-ConfigProductEdition.html)
  * [Get-ConfigProductFeature](Get-ConfigProductFeature.html)
  * [Get-ConfigProductVersion](Get-ConfigProductVersion.html)
  * [Get-ConfigLicensingModel](Get-ConfigLicensingModel.html)
## Parameters

| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| Path | The path to the file containing the feature table | true | false |  |
| Content | Set the site's feature table. | true | true (ByValue) |  |
| LoggingId | Specifies the identifier of the high-level operation this cmdlet call forms a part of. Citrix Studio and Director typically create high-level operations. PowerShell scripts can also wrap a series of cmdlet calls in a high-level operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller the PowerShell snap-in will connect to. You can provide this as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type
### 
   
## Return Values
### 
   
## Examples

### EXAMPLE 1
```
C:\PS> Import-ConfigFeatureTable $xml
```
   Description<br>-----------<br>Specifies the use of a Platinum edition license. A suitable license must be available on the site's license server.
