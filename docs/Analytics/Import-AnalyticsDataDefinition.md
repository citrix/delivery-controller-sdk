# Import-AnalyticsDataDefinition

   This imports a new data definition file for the Analytics Service/Customer Experience Improvement Program.

## Syntax
```
Import-AnalyticsDataDefinition -DataDefinition <String> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
```

## Detailed Description
   The DataDefinition file defines what data should be collected and sent to Citrix. Only Citrix signed DataDefinition files can be imported. An error occurs if the file is not signed properly.

## Related Commands
## Parameters

| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| DataDefinition | The path to a new DataDefinition file | true | false |  |
| LoggingId | Specifies the identifier of the high-level operation this cmdlet call forms a part of. Citrix Studio and Director typically create high-level operations. PowerShell scripts can also wrap a series of cmdlet calls in a high-level operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller the PowerShell snap-in will connect to. You can provide this as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type
### 
   
## Return Values
### 
   
## Examples

### EXAMPLE 1
```
c:\PS>Import-AnalyticsDataDefinition -DataDefinition c:\SignedDataDefinition.xml
```
   Description<br>-----------<br>This imports a new DataDefinition file.
