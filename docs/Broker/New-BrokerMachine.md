# New-BrokerMachine

   Adds a machine that can be used to run desktops and applications.

## Syntax
```
New-BrokerMachine [-MachineName] <String> -CatalogUid <Int32> [-AssignedClientName <String>] [-AssignedIPAddress <String>] [-HostedMachineId <String>] [-HypervisorConnectionUid <Int32>] [-InMaintenanceMode <Boolean>] [-IsReserved <Boolean>] [-UUID <Guid>] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
```

## Detailed Description
   By adding a machine to a catalog, New-BrokerMachine adds a machine to the site, and is the first step in making the machine available to run users' desktops and applications. The machine may be physical or virtual.

For physical machines, you must specify the machine's SID and the catalog to which it will belong. For virtual machines which are not provisioned by MCS, you must also provide the hypervisor connection responsible for running the machine and the hosted machine ID by which the hypervisor recognizes the machine.

The machine must support the expected capabilities of the catalog: the catalog specifies a SessionType and a MinimalFunctionalLevel. The session support of the machine is determined by the type of Citrix VDA software installed (server or workstation) and the functional level depends on the version of the Citrix VDA software installed. The New-BrokerMachine command will complete successfully if these are not correct but the machine will be unable to register.

For more information about machines, see about_Broker_Machines.

## Related Commands
  * [Add-BrokerMachine](Add-BrokerMachine.html)
## Parameters

| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| MachineName | Specify the name of the machine to create (in the form 'domain\machine'). A SID can also be specified. | true | true (ByPropertyName) |  |
| CatalogUid | The catalog to which this machine will belong. | true | true (ByPropertyName) |  |
| AssignedClientName | The client name to which this machine will be assigned. Machines can be assigned to multiple users, a single client IP address, or a single client name, but only to one of these categories at a time. | false | true (ByPropertyName) |  |
| AssignedIPAddress | The client IP address to which this machine will be assigned. Machines can be assigned to multiple users, a single client IP address, or a single client name, but only to one of these categories at a time. | false | true (ByPropertyName) |  |
| HostedMachineId | The unique ID by which the hypervisor recognizes the machine. Omit this for physical machines or MCS-provisioned VMs. | false | true (ByPropertyName) | null |
| HypervisorConnectionUid | The hypervisor connection that runs the machine. Omit this for physical machines or MCS-provisioned VMs. | false | true (ByPropertyName) | null |
| InMaintenanceMode | Specifies whether the machine is initially in maintenance mode. A machine in maintenance mode is not available for new sessions, and for managed machines all automatic power management is disabled. | false | true (ByPropertyName) | false |
| IsReserved | Specifies whether the machine should be reserved for special use, for example, for AppDisk preparation. A reserved machine cannot be added to a desktop group. | false | true (ByPropertyName) |  |
| UUID | An optional GUID for this machine. | false | true (ByPropertyName) | A new GUID is generated if none is supplied. |
| LoggingId | Specifies the identifier of the high level operation that this cmdlet call forms a part of. Desktop Studio and Desktop Director typically create High Level Operations. PowerShell scripts can also wrap a series of cmdlet calls in a High Level Operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |

## Input Type
### None
   You cannot pipe input into this cmdlet.
## Return Values
### Citrix.Broker.Admin.SDK.Machine
   New-BrokerMachine returns the created machine.
## Examples

### EXAMPLE 1
```
C:\PS> New-BrokerMachine -CatalogUid 2 -MachineName 'domain\machine'
```
   Description<br>-----------<br>This adds the physical machine with the specified SAM name to this site and places it in the specified catalog.
### EXAMPLE 2
```
C:\PS> New-BrokerMachine -CatalogUid 2 -MachineName 'S-1-5-12-1234567890-1234567890-1234567890-1234'
```
   Description<br>-----------<br>This adds the physical machine with the specified SID to this site and places it in the specified catalog.
### EXAMPLE 3
```
C:\PS> New-BrokerMachine -CatalogUid 2 -MachineName 'domain\machine' -HostedMachineId 'F8143B4F-7371-4efa-868A-54787EF9F64E' -HypervisorConnectionUid 5
```
   Description<br>-----------<br>This adds the virtual machine, running on the specified hypervisor, to this site and places it in the catalog.
### EXAMPLE 4
```
C:\PS> $m = New-BrokerMachine -CatalogUid 2 -MachineName 'domain\machine'
C:\PS> Add-BrokerMachine -InputObject $m -DesktopGroup 3
```
   Description<br>-----------<br>This adds the specified physical machine to the site and uses Add-BrokerMachine to add it to a desktop group.
