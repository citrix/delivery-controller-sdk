# Set-BrokerApplicationGroupMetadata

   Creates/Updates metadata key-value pairs for ApplicationGroup

## Syntax
```
Set-BrokerApplicationGroupMetadata [-ApplicationGroupId] <Int32> -Name <String> -Value <String> [-PassThru] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]

Set-BrokerApplicationGroupMetadata [-ApplicationGroupId] <Int32> -Name <String> -Value <String> [-PassThru] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]

Set-BrokerApplicationGroupMetadata [-ApplicationGroupId] <Int32> -Map <PSObject> [-PassThru] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]

Set-BrokerApplicationGroupMetadata [-InputObject] <ApplicationGroup[]> -Name <String> -Value <String> [-PassThru] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]

Set-BrokerApplicationGroupMetadata [-InputObject] <ApplicationGroup[]> -Map <PSObject> [-PassThru] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]

Set-BrokerApplicationGroupMetadata [-ApplicationGroupName] <String> -Name <String> -Value <String> [-PassThru] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]

Set-BrokerApplicationGroupMetadata [-ApplicationGroupName] <String> -Map <PSObject> [-PassThru] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
```

## Detailed Description
   The Set-BrokerApplicationGroupMetadata cmdlet creates/updates metadata key-value pairs for ApplicationGroup. The ApplicationGroup can be specified by InputObject or piping.

## Related Commands
## Parameters

| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| ApplicationGroupId | Specifies the ApplicationGroup object whose Metadata is to be created/updated by ID. | true | true (ByValue) |  |
| InputObject | Specifies the ApplicationGroup objects whose Metadata is to be created/updated. | true | true (ByValue) |  |
| ApplicationGroupName | Specifies the ApplicationGroup object whose Metadata is to be created/updated by name. | true | true (ByValue, ByPropertyName) |  |
| Name | Specifies the name of the Metadata member to be created/updated | true | true (ByPropertyName) |  |
| Value | Specifies the value of the Metadata member to be created/updated | true | true (ByPropertyName) |  |
| Map | Specifies a hashtable containing name/value pairs to be used to create or update Metadata members | true | true (ByValue) |  |
| PassThru | This cmdlet does not generate any output, unless you use the PassThru parameter, in which case it returns the affected record. | false | false | False |
| LoggingId | Specifies the identifier of the high level operation that this cmdlet call forms a part of. Desktop Studio and Desktop Director typically create High Level Operations. PowerShell scripts can also wrap a series of cmdlet calls in a High Level Operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |

## Input Type
### Citrix.Broker.Admin.SDK.BrokerApplicationGroup
   You can pipe the ApplicationGroup to hold the new or updated metadata.
## Return Values
### None or Citrix.Broker.Admin.SDK.BrokerApplicationGroup
   This cmdlet does not generate any output, unless you use the PassThru parameter, in which case it generates a Citrix.Broker.Admin.SDK.BrokerApplicationGroup object.
## Examples

### EXAMPLE 1
```
C:\PS> Set-BrokerApplicationGroupMetadata -InputObject $obj-Uid -Name "MyMetadataName" -Value "1234"
```
   Description<br>-----------<br>This command creates/updates the Metadata "MyMetadataName" key-value pair for the ApplicationGroup whose instance is pointed by $obj-Uid
### EXAMPLE 2
```
C:\PS> Get-BrokerApplicationGroup | Set-BrokerApplicationGroupMetadata -Name "MyMetadataName" -Value "1234"
```
   Description<br>-----------<br>This command creates/updates metadata key "MyMetadataName" with the value "1234" for all the ApplicationGroup in the site
### EXAMPLE 3
```
C:\PS> @{ 'name1' = 'value1'; 'name2' = 'value2' } | Set-BrokerApplicationGroupMetadata 'objname'
```
   Description<br>-----------<br>This command creates/updates two metadata keys "name1" and "name2" with the values "value1" and "value2" respectively for the ApplicationGroup in the site whose name is 'objname'
