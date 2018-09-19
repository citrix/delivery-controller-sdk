# Get-HypVolumeServiceConfiguration

   Gets instances of the VolumeServiceConfiguration that are configured for this site.

## Syntax
```
Get-HypVolumeServiceConfiguration [[-VolumeServiceConfigurationName] <String>] [-VolumeServiceConfigurationUid <Guid>] [-ConnectionType <String>] [-Property <String[]>] [-ReturnTotalRecordCount] [-MaxRecordCount <Int32>] [-Skip <Int32>] [-SortBy <String>] [-Filter <String>] [-AdminAddress <String>] [<CommonParameters>]
```

## Detailed Description
   Retrieve VolumeServiceConfigurations whose properties match the given filter criteria. If no parameters are specified, this cmdlet retrieves all VolumeServiceConfiguration objects.

## Related Commands
  * [Set-HypVolumeServiceConfiguration](Set-HypVolumeServiceConfiguration/)
## Parameters

| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| VolumeServiceConfigurationName | Specifies a filter for the configuration name. | false | true (ByValue, ByPropertyName) |  |
| VolumeServiceConfigurationUid | Specifies a filter for the configuration ID. | false | true (ByPropertyName) |  |
| ConnectionType | Specifies a filter for the cloud connection type, such as "AWS" or "CloudPlatform". | false | false |  |
| Property | Specifies the properties to be returned. This is similar to piping the output of the command through Select-Object, but the properties are filtered more efficiently at the server. | false | false |  |
| ReturnTotalRecordCount | When specified, the cmdlet outputs an error record containing the number of records available. This error record is additional information and does not affect the objects written to the output pipeline. See about_Hyp_Filtering for details. | false | false | False |
| MaxRecordCount | Specifies the maximum number of records to return. | false | false | 250 |
| Skip | Skips the specified number of records before returning results. Also reduces the count returned by -ReturnTotalRecordCount. | false | false | 0 |
| SortBy | Sorts the results by the specified list of properties. The list is a set of property names separated by commas, semi-colons, or spaces. Optionally, prefix each name with a + or - to indicate ascending or descending order. Ascending order is assumed if no prefix is present. | false | false | The default sort order is by name or unique identifier. |
| Filter | Gets records that match a PowerShell-style filter expression. See about_Hyp_Filtering for details. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller the PowerShell snap-in will connect to. You can provide this as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type
### string
   The name of a configuration (or set of configurations) to retrieve.
## Return Values
### Citrix.Host.Sdk.VolumeServiceConfiguration
   This cmdlet returns matching VolumeServiceConfiguration objects.
## Examples

### EXAMPLE 1
```
C:\PS>Get-HypVolumeServiceConfiguration -VolumeServiceConfigurationName SiteDefault -ConnectionType CloudPlatform
```
   Description<br>-----------<br>This command lists the site default volume service configuration for connections that use Citrix Cloud Platform.
