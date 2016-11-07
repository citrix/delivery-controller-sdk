# Remove-BrokerConfiguredFTA

   Deletes one or more configured file type associations.

## Syntax
```
Remove-BrokerConfiguredFTA [-InputObject] <ConfiguredFTA[]> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
```

## Detailed Description
   Deletes one or more file type associations configured for a published application. At least one configured file type association object must be specified.

## Related Commands
  * [Get-BrokerConfiguredFTA](Get-BrokerConfiguredFTA.html)
  * [New-BrokerConfiguredFTA](New-BrokerConfiguredFTA.html)
## Parameters

| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| InputObject | Specifies the ConfiguredFTA objects to delete. | true | true (ByValue) |  |
| LoggingId | Specifies the identifier of the high level operation that this cmdlet call forms a part of. Desktop Studio and Desktop Director typically create High Level Operations. PowerShell scripts can also wrap a series of cmdlet calls in a High Level Operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |

## Input Type
### Citrix.Broker.Admin.SDK.ConfiguredFTA[]
   One or more ConfiguredFTA objects can be supplied as input.
## Return Values
### None
   
## Examples

### EXAMPLE 1
```
C:\PS> $ftas = Get-BrokerConfiguredFTA -ExtensionName ".txt"
C:\PS> Remove-BrokerConfiguredFTA $ftas
```
   Description<br>-----------<br>Deletes all configured file type associations with an extension name of ".txt".
