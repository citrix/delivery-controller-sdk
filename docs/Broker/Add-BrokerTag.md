# Add-BrokerTag

   Associate a tag with another object in the site.

## Syntax
```
Add-BrokerTag [-InputObject] <Tag[]> [-Application <Application>] [-ApplicationGroup <ApplicationGroup>] [-Desktop <Desktop>] [-DesktopGroup <DesktopGroup>] [-Machine <Machine>] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]

Add-BrokerTag [-Name] <String> [-Application <Application>] [-ApplicationGroup <ApplicationGroup>] [-Desktop <Desktop>] [-DesktopGroup <DesktopGroup>] [-Machine <Machine>] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
```

## Detailed Description
   Associates one or more tags with a machine, application group, application, desktop group or desktop within the site.

## Related Commands
  * [Get-BrokerTag](Get-BrokerTag.html)
  * [New-BrokerTag](New-BrokerTag.html)
  * [Remove-BrokerTag](Remove-BrokerTag.html)
  * [Rename-BrokerTag](Rename-BrokerTag.html)
  * [Set-BrokerTag](Set-BrokerTag.html)
## Parameters

| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| InputObject | Specifies one or more tag objects. | true | true (ByValue) |  |
| Name | Specifies a tag by name. | true | true (ByPropertyName) |  |
| Application | Associates the tag with the specified application. | false | true (ByValue) |  |
| ApplicationGroup | Associates the tag with the specified application group. | false | true (ByValue) |  |
| Desktop | Associates the tag with the specified desktop. The tag is associated with the underlying machine not with the desktop itself.<br>This parameter is deprecated, use -Machine instead. | false | true (ByValue) |  |
| DesktopGroup | Associates the tag with the specified desktop group. | false | true (ByValue) |  |
| Machine | Associates the tag with the specified machine. | false | true (ByValue) |  |
| LoggingId | Specifies the identifier of the high level operation that this cmdlet call forms a part of. Desktop Studio and Desktop Director typically create High Level Operations. PowerShell scripts can also wrap a series of cmdlet calls in a High Level Operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |

## Input Type
### Citrix.Broker.Admin.SDK.Tag
   Tags may be specified through pipeline input.
## Return Values
### None
   
## Examples

### EXAMPLE 1
```
C:\PS> Add-BrokerTag -Name 'Tag1' -Machine DOMAIN\Machine
```
   Description<br>-----------<br>Associates 'Tag1' with machine DOMAIN\Machine.
### EXAMPLE 2
```
C:\PS> $machine = Get-BrokerMachine -Uid 1
C:\PS> New-BrokerTag 'Tag2' | Add-BrokerTag -Machine $machine
```
   Description<br>-----------<br>Creates a new tag with name 'Tag2' and associates it with the machine with Uid 1.
