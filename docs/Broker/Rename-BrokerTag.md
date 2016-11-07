# Rename-BrokerTag

   Rename one or more tags.

## Syntax
```
Rename-BrokerTag [-InputObject] <Tag[]> [-NewName] <String> [-PassThru] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]

Rename-BrokerTag [-Name] <String> [-NewName] <String> [-PassThru] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
```

## Detailed Description
   Renames one or more tags with the supplied name.

## Related Commands
  * [Add-BrokerTag](Add-BrokerTag.html)
  * [Get-BrokerTag](Get-BrokerTag.html)
  * [New-BrokerTag](New-BrokerTag.html)
  * [Remove-BrokerTag](Remove-BrokerTag.html)
  * [Set-BrokerTag](Set-BrokerTag.html)
## Parameters

| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| InputObject | Specifies one or more tag objects to rename. | true | true (ByValue) |  |
| Name | Identifies tags to be renamed by name. | true | true (ByPropertyName) |  |
| NewName | Specifies new name for the tags. | true | false |  |
| PassThru | This cmdlet does not generate any output, unless you use the PassThru parameter, in which case it returns the affected record. | false | false | False |
| LoggingId | Specifies the identifier of the high level operation that this cmdlet call forms a part of. Desktop Studio and Desktop Director typically create High Level Operations. PowerShell scripts can also wrap a series of cmdlet calls in a High Level Operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |

## Input Type
### Citrix.Broker.Admin.SDK.Tag
   The tag to rename can be piped into this cmdlet.
## Return Values
### None or Citrix.Broker.Admin.SDK.Tag
   This cmdlet does not generate any output, unless you use the PassThru parameter, in which case it generates a Citrix.Broker.Admin.SDK.Tag object.## Notes
   Note that when renaming a tag, its UUID remains the same and any associations are maintained.
## Examples

### EXAMPLE 1
```
C:\PS> Rename-BrokerTag -Name 'OldName' -NewName 'ReplacementName'
```
   Description<br>-----------<br>Renames tags with the name 'OldName' to 'ReplacementName'.
