# Get-BrokerConfigurationSlot

   Gets configuration slots configured for this site.

## Syntax
```
Get-BrokerConfigurationSlot [-Uid] <Int32> [-Property <String[]>] [-AdminAddress <String>] [<CommonParameters>]

Get-BrokerConfigurationSlot [[-Name] <String>] [-Metadata <String>] [-ReturnTotalRecordCount] [-MaxRecordCount <Int32>] [-Skip <Int32>] [-SortBy <String>] [-Filter <String>] [-Property <String[]>] [-AdminAddress <String>] [<CommonParameters>]
```

## Detailed Description
   Get the list of configuration slots defined for this site. Each configuration slot determines a collection of related settings that can be specified in a machine configuration associated with this slot.

For example, a configuration slot may be defined to configure only "User Profile Manager" settings.

See about_Broker_Filtering for information about advanced filtering options.


-------------------------- BrokerConfigurationSlot Object
The configuration slot object returned represents a named collection of related settings.

    -- Description (System.String)
       Optional description of this configuration slot.

    -- MetadataMap (System.Collections.Generic.Dictionary<string, string>)
       A map of metadata associated with this configuration slot.

    -- Name (System.String)
       Unique name of this configuration slot.

    -- SettingsGroup (System.String)
       The encoded identity of the settings group that every setting in the associated machine configuration instances must belong to.

    -- Uid (System.Int32)
       Unique Uid of this configuration slot.

## Related Commands
  * [New-BrokerConfigurationSlot](New-BrokerConfigurationSlot.html)
  * [Remove-BrokerConfigurationSlot](Remove-BrokerConfigurationSlot.html)
  * [Get-BrokerMachineConfiguration](Get-BrokerMachineConfiguration.html)
## Parameters

| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| Uid | Get only the configuration slot with the specified unique identifier. | true | false |  |
| Name | Get only the configuration slot with the specified name. | false | false |  |
| Metadata | Gets records with matching metadata entries.<br>The value being compared with is a concatenation of the key name, a colon, and the value. For example: -Metadata "abc:x*" matches records with a metadata entry having a key name of "abc" and a value starting with the letter "x". | false | false |  |
| ReturnTotalRecordCount | When specified, this causes the cmdlet to output an error record containing the number of records available. This error record is additional information and does not affect the objects written to the output pipeline. See about_Broker_Filtering for details. | false | false | False |
| MaxRecordCount | Specifies the maximum number of records to return. | false | false | 250 |
| Skip | Skips the specified number of records before returning results. Also reduces the count returned by -ReturnTotalRecordCount. | false | false | 0 |
| SortBy | Sorts the results by the specified list of properties. The list is a set of property names separated by commas, semi-colons, or spaces. Optionally, prefix each name with a + or - to indicate ascending or descending order. Ascending order is assumed if no prefix is present. | false | false | The default sort order is by name or unique identifier. |
| Filter | Gets records that match a PowerShell style filter expression. See about_Broker_Filtering for details. | false | false |  |
| Property | Specifies the properties to be returned. This is similar to piping the output of the command through Select-Object, but the properties are filtered more efficiently at the server. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |

## Input Type
### None
   You cannot pipe input into this cmdlet.
## Return Values
### Citrix.Broker.Admin.SDK.ConfigurationSlot
   Get-BrokerConfigurationSlot returns an object for each matching slot.
## Examples

### EXAMPLE 1
```
Get-ConfigurationSlot
```
   Description<br>-----------<br>Retrieves every configuration slot.
### EXAMPLE 2
```
Get-ConfigurationSlot -Name "AppV"
```
   Description<br>-----------<br>Retrieves the configuration slot named "AppV".
