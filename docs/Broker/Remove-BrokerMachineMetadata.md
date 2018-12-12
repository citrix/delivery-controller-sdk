﻿
# Remove-Brokermachinemetadata
Deletes Machine Metadata from the Machine objects
## Syntax
```
Remove-BrokerMachineMetadata [-InputObject] <Machine[]> -Name <String> [-LoggingId <Guid>] [-AdminAddress <String>] [-BearerToken <String>] [<CommonParameters>]
```
## Detailed Description
The Remove-BrokerMachineMetadata cmdlet deletes Metadata from the Machine objects.


## Related Commands

## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| InputObject | Specifies the Machine object's instance whose Metadata is to be deleted. | true | true (ByValue) |  |
| Name | Specifies the name of the Metadata to be deleted | true | false |  |
| LoggingId | Specifies the identifier of the high level operation that this cmdlet call forms a part of. Desktop Studio and Desktop Director typically create High Level Operations. PowerShell scripts can also wrap a series of cmdlet calls in a High Level Operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |

## Input Type

### Citrix.Broker.Admin.Sdk.Brokermachine
You can pipe the Machine to delete the metadata.
## Return Values

### None

## Examples

### Example 1
```
C:\PS> Remove-BrokerMachineMetadata -InputObject $obj-Uid -Name "MyMetadataName"
```
#### Description
This command deletes the Metadata "MyMetadataName" key-value pair for the Machine whose instance is pointed by \$obj-Uid
### Example 2
```
C:\PS> Get-BrokerMachine | Remove-BrokerMachineMetadata -Name "MyMetadataName"
```
#### Description
This command deletes the Metadata "MyMetadataName" key-value pair for all the Machine in the site
