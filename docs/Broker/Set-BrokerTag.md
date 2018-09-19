# Set-BrokerTag

   Sets the properties of a tag.

## Syntax
```
Set-BrokerTag [-InputObject] <Tag[]> [-PassThru] [-Description <String>] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]

Set-BrokerTag [-Name] <String> [-PassThru] [-Description <String>] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
```

## Detailed Description
   The Set-BrokerTag cmdlet sets properties of a tag or set of tags. The tags on which to operate can be specified by name, in which case multiple tags may be specified through the use of wildcards, or by passing one or more Tag instances to the cmdlet by piping or by using the -InputObject parameter.

## Related Commands
  * [Add-BrokerTag](Add-BrokerTag/)
  * [Get-BrokerTag](Get-BrokerTag/)
  * [New-BrokerTag](New-BrokerTag/)
  * [Remove-BrokerTag](Remove-BrokerTag/)
  * [Rename-BrokerTag](Rename-BrokerTag/)
## Parameters

| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| InputObject | Specifies the tag objects to modify. | true | true (ByValue) |  |
| Name | Identifies the tag to modify. | true | true (ByPropertyName) |  |
| PassThru | This cmdlet does not generate any output, unless you use the PassThru parameter, in which case it returns the affected record. | false | false | False |
| Description | Supplies the new value of the Description property. | false | false |  |
| LoggingId | Specifies the identifier of the high level operation that this cmdlet call forms a part of. Desktop Studio and Desktop Director typically create High Level Operations. PowerShell scripts can also wrap a series of cmdlet calls in a High Level Operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |

## Input Type
### Citrix.Broker.Admin.SDK.Tag
   You can pipe the tags to be modified to Set-BrokerTag.
## Return Values
### None or Citrix.Broker.Admin.SDK.Tag
   This cmdlet does not generate any output, unless you use the PassThru parameter, in which case it generates a Citrix.Broker.Admin.SDK.Tag object.## Notes
   A tag's Name property cannot be changed by Set-BrokerTag. To rename a tag use Rename-BrokerTag.
## Examples

### EXAMPLE 1
```
C:\PS> $mytag = Get-BrokerTag MyTag
C:\PS> Set-BrokerTag -InputObject $mytag -Description "This is my tag. I use it to label all my things."
```
   Description<br>-----------<br>This example sets the description for the existing tag MyTag.
