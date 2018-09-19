# Remove-HypHostingUnitStorage

   Removes storage from a hosting unit.

## Syntax
```
Remove-HypHostingUnitStorage [-LiteralPath] <String> [-StoragePath <String>] [-StorageType <StorageType>] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
```

## Detailed Description
   Use this command to remove storage locations from a hosting unit. This does not remove the storage from the hypervisor, only the reference to the storage for the Host Service. After removal, the storage is no longer used to store hard disks (when creating new virtual machines with the Machine Creation Service). The hard disks located already on the storage remain in place and virtual machines that have been created already continue to use the storage until they are removed from the deployment. Do not use this command if the connection for the hosting unit is in maintenance mode. If the storage location to be removed no longer exists on the hypervisor for the hosting unit, you must supply a fully qualified path to the storage location.

## Related Commands
  * [Add-HypHostingUnitStorage](Add-HypHostingUnitStorage/)
  * [Set-HypHostingUnitStorage](Set-HypHostingUnitStorage/)
  * [New-Item](New-Item/)
  * [Add-HypMetadata](Add-HypMetadata/)
## Parameters

| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| LiteralPath | Specifies the path to the hosting unit which defines the storage. The path must be in one of the following formats: <drive>:\HostingUnits\<HostingUnitName> or  <drive>:\HostingUnits\{<HostingUnit Uid>} | true | false |  |
| StoragePath | Specifies the path in the hosting unit provider of the storage to remove. If StoragePath is not specified, all storage is removed from the hosting unit. The path must be in one of the following formats: <drive>:\Connections\<ConnectionName>\MyStorage.storage or  <drive>:\Connections\{<Connection Uid>}\MyStorage.storage or  <drive>:\HostingUnits\<HostingUnitName>\MyStorage.storage or  <drive>:\HostingUnits\{<hostingUnit Uid>}\MyStorage.storage | false | true (ByValue) |  |
| StorageType | Specifies the type of storage in StoragePath. Supported storage types are: OSStorage PersonalvDiskStorage TemporaryStorage | false | false | OSStorage |
| LoggingId | Specifies the identifier of the high-level operation this cmdlet call forms a part of. Citrix Studio and Director typically create high-level operations. PowerShell scripts can also wrap a series of cmdlet calls in a high-level operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snap-in connects to. This can be a host name or an IP address. | false | false | LocalHost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type
### System.string<br>    You can pipe a string that contains a path to Remove-HypHostingUnitStorage (StoragePath parameter).
   
## Return Values
### Citrix.XDPowerShell.HostingUnit<br>    Remove-HypHostingUnitStorage returns an object containing the new definition of the hosting unit.<br>    HostingUnitUid <Guid><br>        Specifies the unique identifier for the hosting unit.<br>    HostingUnitName <string><br>        Specifies the name of the hosting unit.<br>    HypervisorConnection <Citrix.XDPowerShell.HypervisorConnection><br>        Specifies the connection that the hosting unit uses to access a hypervisor.<br>    RootId <string><br>        Identifies, to the hypervisor, the root of the hosting unit.<br>    RootPath <string><br>        The hosting unit provider path that represents the root of the hosting unit.<br>    Storage <Citrix.XDPowerShell.Storage[]><br>        The list of storage items that the hosting unit can use.<br>    PersonalvDiskStorage <Citrix.XDPowerShell.Storage[]><br>        The list of storage items that the hosting unit can use for storing personal data.<br>    VMTaggingEnabled <Boolean><br>        Specifies whether or not the metadata in the hypervisor can be used to store information about the XenDesktop Machine Creation Service.<br>    NetworkId <string><br>        The hypervisor's internal identifier that represents the network specified for the hosting unit.<br>    NetworkPath <string><br>        The hosting unit provider path to the network specified for the hosting unit.<br>    AdditionalStorage<br>        The list of additional storage items that the hosting unit can use.<br>    Metadata <Citrix.XDPowerShell.Metadata[]><br>        A list of key value pairs that can store additional information about the hosting unit.
   ## Notes
   After storage is removed, it is the administrator's responsibility to maintain its contents. The Citrix XenDesktop Machine Creation Service does not attempt to clean up any data that is stored in the storage location.<br>    If all storage is removed from the hosting unit, other features of the Machine Creation Service stops functioning until some storage is added again.<br>    In the case of failure, the following errors can result.<br>    Error Codes<br>    -----------<br>    HostingUnitsPathInvalid<br>    The path provided is not to an item in a subdirectory of a hosting unit item.<br>    HostingUnitStorageObjectToDeleteDoesNotExist<br>    The storage path specified is not part of the hosting unit.<br>    HypervisorInMaintenanceMode<br>    The hypervisor for the connection is in maintenance mode.<br>    DatabaseError<br>    An error occurred in the service while attempting a database operation.<br>    DatabaseNotConfigured<br>    The operation could not be completed because the database for the service is not configured.<br>    DataStoreException<br>    An error occurred in the service while attempting a database operation. Communication with the database failed for<br>    for various reasons.<br>    CommunicationError<br>    An error occurred while communicating with the service.<br>    PermissionDenied<br>    The user does not have administrative rights to perform this operation.<br>    ExceptionThrown<br>    An unexpected error occurred. To locate more details, see the Windows event logs on the controller being used, or examine the XenDesktop logs.
## Examples

### EXAMPLE 1
```
c:\PS>Remove-HypHostingUnitStorage -LiteralPath XDHyp:\HostingUnits\MyHostingUnit -StoragePath 'XDHyp:\HostingUnits\MyHostingUnits\newStorage.storage'
```
   Description<br>-----------<br>The command removes the OS storage location called "newStorage.storage" from the hosting unit called "MyHostingUnit"
### EXAMPLE 2
```
c:\PS>Get-ChildItem XDHYP:\HostingUnits\Host\*.storage | Remove-HypHostingUnitStorage XDHYP:\HostingUnits\Host1
```
   Description<br>-----------<br>The command removes all OS storage from all hosting units called "Host1".
### EXAMPLE 3
```
c:\PS>Get-ChildItem XDHYP:\HostingUnits\Host\*.storage | Remove-HypHostingUnitStorage -StorageType PersonalvDiskStorage
```
   Description<br>-----------<br>The command removes all PersonalvDisk storage from all hosting units called "Host1".
