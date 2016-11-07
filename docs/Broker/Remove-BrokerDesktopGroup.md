# Remove-BrokerDesktopGroup

   Remove desktop groups from the system or remove them from a Remote PC catalog.

## Syntax
```
Remove-BrokerDesktopGroup [-InputObject] <DesktopGroup[]> [-Force] [-RemotePCCatalog <Catalog>] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]

Remove-BrokerDesktopGroup [-Name] <String> [-Force] [-RemotePCCatalog <Catalog>] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
```

## Detailed Description
   This cmdlet has 2 functions:

o Remove desktop groups from the system.
o Break Remote PC associations between desktop groups and a catalog.

The Remote PC relationships are used by Remote PC automation to determine which desktop groups a machine in a particular Remote PC catalog can be published to. The assignment policy rules belonging to those desktop groups also determines the set of users that are allowed to be assigned to machines from the catalog.

## Related Commands
  * [Get-BrokerDesktopGroup](Get-BrokerDesktopGroup.html)
  * [New-BrokerDesktopGroup](New-BrokerDesktopGroup.html)
  * [Set-BrokerDesktopGroup](Set-BrokerDesktopGroup.html)
  * [Add-BrokerDesktopGroup](Add-BrokerDesktopGroup.html)
  * [Rename-BrokerDesktopGroup](Rename-BrokerDesktopGroup.html)
  * [New-BrokerCatalog](New-BrokerCatalog.html)
  * [Remove-BrokerCatalog](Remove-BrokerCatalog.html)
## Parameters

| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| InputObject | Specifies the desktop groups to remove. | true | true (ByValue) | null |
| Name | Specifies the name of the desktop group to remove. | true | true (ByPropertyName) | null |
| Force | Remove desktop groups even if there are active sessions. | false | false | false |
| RemotePCCatalog | When this parameter is specified, Remote PC desktop groups are removed from the specified Remote PC catalog. | false | true (ByValue) | null |
| LoggingId | Specifies the identifier of the high level operation that this cmdlet call forms a part of. Desktop Studio and Desktop Director typically create High Level Operations. PowerShell scripts can also wrap a series of cmdlet calls in a High Level Operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |

## Input Type
### Citrix.Broker.Admin.SDK.DesktopGroup
   You can pipe desktop groups to Remove-BrokerDesktopGroup.
## Return Values
### None
   ## Notes
   If a desktop group contains desktops when it is removed, these desktops are also removed (but the underlying broker machine remains).<br>    A desktop group that still has active sessions cannot be removed unless the -Force switch is used.
## Examples

### EXAMPLE 1
```
C:\PS> Remove-BrokerDesktopGroup EMEA*
```
   Description<br>-----------<br>Remove all desktop groups with names starting with "EMEA".
### EXAMPLE 2
```
C:\PS> Get-BrokerDesktopGroup -Enabled $false | Remove-BrokerDesktopGroup -Force
```
   Description<br>-----------<br>Remove all desktops that are currently disabled even if there are active sessions.
### EXAMPLE 3
```
C:\PS> Get-BrokerDesktopGroup -RemotePCCatalogUid 42 | Remove-BrokerDesktopGroup -RemotePCCatalog 42
```
   Description<br>-----------<br>Remove all the Remote PC desktop groups that are associated with catalog 42. Note that this only breaks the Remote PC relationships and does not delete the desktop groups.
