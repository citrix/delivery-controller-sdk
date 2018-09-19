# Get-BrokerTag

   Gets one or more tags.

## Syntax
```
Get-BrokerTag [-Uid] <Int32> [-Property <String[]>] [-AdminAddress <String>] [<CommonParameters>]

Get-BrokerTag [[-Name] <String>] [-Description <String>] [-Metadata <String>] [-UUID <Guid>] [-ApplicationUid <Int32>] [-ApplicationGroupUid <Int32>] [-DesktopUid <Int32>] [-DesktopGroupUid <Int32>] [-MachineUid <Int32>] [-ReturnTotalRecordCount] [-MaxRecordCount <Int32>] [-Skip <Int32>] [-SortBy <String>] [-Filter <String>] [-Property <String[]>] [-AdminAddress <String>] [<CommonParameters>]
```

## Detailed Description
   Gets tags that match all of the supplied criteria.


-------------------------- BrokerTag Object
The BrokerTag object represents a single instance of a Tag associated to other objects. It contains the following properties:

    -- Description (System.String)
       Description of the tag.

    -- MetadataMap (System.Collections.Generic.Dictionary<string, string>)
       The metadata for this command.

    -- Name (System.String)
       The name of the Tag

    -- Uid (System.Int32)
       The Uid of the Tag

    -- UUID (System.Guid)
       The UUID associated to the Tag

## Related Commands
  * [Add-BrokerTag](Add-BrokerTag/)
  * [New-BrokerTag](New-BrokerTag/)
  * [Remove-BrokerTag](Remove-BrokerTag/)
  * [Rename-BrokerTag](Rename-BrokerTag/)
  * [Set-BrokerTag](Set-BrokerTag/)
## Parameters

| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| Uid | Gets the tag identified by Uid | true | false |  |
| Name | Gets tags that match the specified name. | false | false |  |
| Description | Gets tags with the specified description. | false | false |  |
| Metadata | Gets records with matching metadata entries.<br>The value being compared with is a concatenation of the key name, a colon, and the value. For example: -Metadata "abc:x*" matches records with a metadata entry having a key name of "abc" and a value starting with the letter "x". | false | false |  |
| UUID | Gets tags associated with a given UUID. | false | false |  |
| ApplicationUid | Gets tags associated with the specified application. | false | false |  |
| ApplicationGroupUid | Get tags associated with the specified application group. | false | false |  |
| DesktopUid | Gets tags associated with the specified desktop. | false | false |  |
| DesktopGroupUid | Gets tags associated with the specified desktop group. | false | false |  |
| MachineUid | Gets tags associated with the specified machine. | false | false |  |
| ReturnTotalRecordCount | When specified, this causes the cmdlet to output an error record containing the number of records available. This error record is additional information and does not affect the objects written to the output pipeline. See about_Broker_Filtering for details. | false | false | False |
| MaxRecordCount | Specifies the maximum number of records to return. | false | false | 250 |
| Skip | Skips the specified number of records before returning results. Also reduces the count returned by -ReturnTotalRecordCount. | false | false | 0 |
| SortBy | Sorts the results by the specified list of properties. The list is a set of property names separated by commas, semi-colons, or spaces. Optionally, prefix each name with a + or - to indicate ascending or descending order. Ascending order is assumed if no prefix is present. | false | false | The default sort order is by name or unique identifier. |
| Filter | Gets records that match a PowerShell style filter expression. See about_Broker_Filtering for details. | false | false |  |
| Property | Specifies the properties to be returned. This is similar to piping the output of the command through Select-Object, but the properties are filtered more efficiently at the server. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |

## Input Type
### None
   Input cannot be piped to this cmdlet.
## Return Values
### Citrix.Broker.Admin.SDK.Tag
   Returns matching tags.
## Examples

### EXAMPLE 1
```
C:\PS> Get-BrokerTag
```
   Description<br>-----------<br>Enumerate all tags.
### EXAMPLE 2
```
C:\PS> Get-BrokerTag -Uid 5
```
   Description<br>-----------<br>Get a single specific tag with a Uid of 5.
### EXAMPLE 3
```
C:\PS> $machine = Get-BrokerMachine DOMAIN\Machine
C:\PS> Get-BrokerTag -MachineUid $machine.Uid
```
   Description<br>-----------<br>Get tags associated with machine DOMAIN\Machine.
