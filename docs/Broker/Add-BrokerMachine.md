# Add-BrokerMachine

   Adds one or more machines to a desktop group.

## Syntax
```
Add-BrokerMachine [-InputObject] <Machine[]> [-DesktopGroup <DesktopGroup>] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]

Add-BrokerMachine [-MachineName] <String> [-DesktopGroup <DesktopGroup>] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
```

## Detailed Description
   The Add-BrokerMachine cmdlet adds specified machines to a desktop group. There are three forms:


o Use the -InputObject parameter to add a single machine instance or array of instances to the group.
o Use the -MachineName parameter to add a single, named machine to the group.
o Use pipelining to pipe machines instances to the command.

The desktop group to which the machines are added can be specified by name, unique identifier (UID), or instance.

For a machine to be used in a site, the machine must be added to a desktop group. The machine and desktop group must be compatible in order for the process to succeed; for example a machine in a single-session catalog cannot be added to a multi-session desktop group.

For more information about machines, see about_Broker_Machines.

## Related Commands
  * [Add-BrokerMachinesToDesktopGroup](Add-BrokerMachinesToDesktopGroup.html)
  * [Remove-BrokerMachine](Remove-BrokerMachine.html)
  * [Get-BrokerMachine](Get-BrokerMachine.html)
## Parameters

| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| InputObject | An array of machines to add to the group. | true | true (ByValue) |  |
| MachineName | The name of the single machine to add (must match the MachineName property of the machine). | true | true (ByPropertyName) |  |
| DesktopGroup | The desktop group to which the machines are added, specified by name, Uid, or instance. | false | true (ByValue) |  |
| LoggingId | Specifies the identifier of the high level operation that this cmdlet call forms a part of. Desktop Studio and Desktop Director typically create High Level Operations. PowerShell scripts can also wrap a series of cmdlet calls in a High Level Operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |

## Input Type
### Citrix.Broker.Admin.SDK.Machine
   You can pipe in the machines you want to add.
## Return Values
### None
   
## Examples

### EXAMPLE 1
```
C:\PS> Add-BrokerMachine -InputObject $machine -DesktopGroup $desktopGroup
C:\PS> Add-BrokerMachine -InputObject $machine -DesktopGroup 2
C:\PS> Add-BrokerMachine $machine -DesktopGroup "MyDesktopGroup"
```
   Description<br>-----------<br>These examples all add a single machine instance to a desktop group, identifying the group by instance, UID, or name.
### EXAMPLE 2
```
C:\PS> Add-BrokerMachine -MachineName "MyDomain\MyMachine" -DesktopGroup 2
C:\PS> Add-BrokerMachine "MyDomain\MyMachine" -DesktopGroup "MyDesktopGroup"
C:\PS> Add-BrokerMachine "MyDomain\MyMachine" -DesktopGroup $desktopGroup
```
   Description<br>-----------<br>These examples add the machine called MyMachine to a desktop group.
### EXAMPLE 3
```
C:\PS> Get-BrokerMachine -Uid 3 | Add-BrokerMachine -DesktopGroup 2
C:\PS> Get-BrokerMachine -CatalogUid 4 | Add-BrokerMachine -DesktopGroup 2
```
   Description<br>-----------<br>These examples find specific machines and add them to a desktop group.
