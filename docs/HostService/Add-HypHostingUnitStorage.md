# Add-HypHostingUnitStorage

   Adds storage locations to a hosting unit.

## Syntax
```
Add-HypHostingUnitStorage [-LiteralPath] <String> [-StoragePath] <String> [-StorageType <StorageType>] [-LoggingId <Guid>] [-BearerToken <String>] [-AdminAddress <String>] [<CommonParameters>]
```

## Detailed Description
   Use this command to add storage locations for storing the hard disks required by the virtual machines created by the Citrix Machine Creation Service. You cannot use this command if the connection for the hosting unit is in maintenance mode.

## Related Commands
  * [New-Item](New-Item.html)
  * [Add-HypMetadata](Add-HypMetadata.html)
  * [Remove-HypHostingUnitStorage](Remove-HypHostingUnitStorage.html)
  * [Set-HypHostingUnitStorage](Set-HypHostingUnitStorage.html)
## Parameters

| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| LiteralPath | Specifies the path to the hosting unit to which storage will be added. The path must be in one of the following formats: <drive>:\HostingUnits\<HostingUnitName> or  <drive>:\HostingUnits\{<HostingUnit Uid>} | true | false |  |
| StoragePath | Specifies the path to the storage that will be added. The path must be in one of the following formats: <drive>:\Connections\<ConnectionName>\MyStorage.storage or  <drive>:\Connections\{<Connection Uid>}\MyStorage.storage or  <drive>:\HostingUnits\<HostingUnitName>\MyStorage.storage or  <drive>:\HostingUnits\{<hostingUnit Uid>}\MyStorage.storage | true | true (ByValue) |  |
| StorageType | Specifies the type of storage in StoragePath. Supported storage types are: OSStorage PersonalvDiskStorage TemporaryStorage | false | false | OSStorage |
| LoggingId | Specifies the identifier of the high-level operation this cmdlet call forms a part of. Citrix Studio and Director typically create high-level operations. PowerShell scripts can also wrap a series of cmdlet calls in a high-level operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller to which the PowerShell snap-in connects. This can be a host name or an IP address. | false | false | LocalHost. When a value is provided by any cmdlet, this value becomes the default. |

## Input Type
### System.string<br>    You can pipe a string that contains a path to Add-HypHostingUnitStorage (StoragePath parameter).
   
## Return Values
### Citrix.Host.Sdk.HostingUnit<br>    Add-HypHostingUnitStorage returns an object containing the new definition of the hosting unit.<br>    HostingUnitUid <Guid><br>        Specifies the unique identifier for the hosting unit.<br>    HostingUnitName <string><br>        Specifies the name of the hosting unit.<br>    HypervisorConnection <Citrix.Host.Sdk.HypervisorConnection><br>        Specifies the connection that the hosting unit uses to access a hypervisor.<br>    RootId <string><br>        Identifies, to the hypervisor, the root of the hosting unit.<br>    RootPath <string><br>        The hosting unit provider path that represents the root of the hosting unit.<br>    Storage <Citrix.Host.Sdk.Storage[]><br>        The list of storage items that the hosting unit can use.<br>    PersonalvDiskStorage <Citrix.XDPowerShell.Storage[]><br>        The list of storage items that the hosting unit can use for storing personal data.<br>    VMTaggingEnabled <Boolean><br>        Specifies whether or not the metadata in the hypervisor can be used to store information about the XenDesktop Machine Creation Service.<br>    NetworkId <string><br>        The hypervisor's internal identifier that represents the network specified for the hosting unit.<br>    NetworkPath <string><br>        The hosting unit provider path to the network specified for the hosting unit.<br>    AdditionalStorage<br>        The list of additional storage items that the hosting unit can use.<br>    Metadata <Citrix.Host.Sdk.Metadata[]><br>        A list of key value pairs that can store additional information about the hosting unit.
   ## Notes
   The storage path must be valid for the hosting unit. The rules that are applied are as follows: XenServer (HypervisorConnection Type = XenServer)<br>    NA<br>    VMWare vSphere/ESX (HypervisorConnection Type = vCenter)<br>    The storage path must be directly contained in the root path item of the hosting unit.<br>    Microsoft SCVMM/Hyper-v (HypervisorConnection Type = SCVMM)<br>    Only one storage entry for these connection types is valid, and it must reference an SMB share. Additionally, if a Hyper-V failover cluster is used the SMB share must be the top-level mount point of the cluster shared volume on one of the servers in the cluster (i.e. C:\ClusterStorage).<br>    In the case of failure, the following errors can result.<br>    Error Codes<br>    -----------<br>    HostingUnitsPathInvalid<br>    The path provided is not to an item in a subdirectory of a hosting unit item.<br>    HostingUnitStoragePathInvalid<br>    The specified path is invalid.<br>    HostingUnitStoragePathInvalid<br>    The storage path cannot be found or is invalid. See notes above about validity.<br>    HostingUnitStorageDuplicateObjectExists<br>    The specified storage path is already part of the hosting unit.<br>    HypervisorInMaintenanceMode<br>    The hypervisor for the connection is in maintenance mode.<br>    DatabaseError<br>    An error occurred in the service while attempting a database operation.<br>    DatabaseNotConfigured<br>    The operation could not be completed because the database for the service is not configured.<br>    DataStoreException<br>    An error occurred in the service while attempting a database operation. Communication with the database failed for<br>    various reasons.<br>    CommunicationError<br>    An error occurred while communicating with the service.<br>    PermissionDenied<br>    The user does not have administrative rights to perform this operation.<br>    ExceptionThrown<br>    An unexpected error occurred. To locate more details, see the Windows event logs on the controller being used, or examine the XenDesktop logs.
## Examples

### EXAMPLE 1
```
c:\PS>Add-HypHostingUnitStorage -LiteralPath XDHyp:\HostingUnits\MyHostingUnit -StoragePath 'XDHyp:\HostingUnits\MyHostingUnits\newStorage.storage'

          HostingUnitUid       : bcd3d649-86d1-4aa8-8ec2-d322b6a2c457
          HostingUnitName      : MyHostingUnit
          HypervisorConnection : MyConnection
          RootPath             : /
          RootId               :
          NetworkPath          : /Network 0.network
          NetworkId            : ab47080b-ca15-771a-c8dc-6ad9650158f1
          Storage              : {/Local storage.storage, /newStorage.storage}
          PersonalvDiskStorage : {/newStorage.storage}
          VMTaggingEnabled     : True
          AdditionalStorage    : {TemporaryStorage}
          Metadata             : {}
```
   Description<br>-----------<br>The command adds a new storage location called "newStorage.storage" to the hosting unit called "MyHostingUnit".
### EXAMPLE 2
```
XDHyp:\HostingUnits\MyHostingUnit>Add-HypHostingUnitStorage -LiteralPath . -StoragePath 'XDHyp:\HostingUnits\MyHostingUnits\newStorage.storage' -StorageType OSStorage

          HostingUnitUid       : bcd3d649-86d1-4aa8-8ec2-d322b6a2c457
          HostingUnitName      : MyHostingUnit
          HypervisorConnection : MyConnection
          RootPath             : /
          RootId               :
          NetworkPath          : /Network 0.network
          NetworkId            : ab47080b-ca15-771a-c8dc-6ad9650158f1
          Storage              : {/Local storage.storage, /newStorage.storage}
          PersonalvDiskStorage : {/Local storage.storage}
          VMTaggingEnabled     : True
          AdditionalStorage    : {TemporaryStorage}
          Metadata             : {}
```
   Description<br>-----------<br>The command adds a new storage location called "newStorage.storage" to the current directory. The dot (.) represents the current location (not its contents).
### EXAMPLE 3
```
XDHyp:\HostingUnits\MyHostingUnit>dir *.storage | Add-HypHostingUnitStorage -LiteralPath XDHyp:\HostingUnits\MyHostingUnit
```
   Description<br>-----------<br>The command adds all of the storage that is available in the hosting unit to the specified hosting unit.
### EXAMPLE 4
```
c:\PS>Add-HypHostingUnitStorage -LiteralPath XDHyp:\HostingUnits\MyHostingUnit -StoragePath 'XDHyp:\HostingUnits\MyHostingUnits\newStorage.storage' -StorageType PersonalvDiskStorage

          HostingUnitUid       : bcd3d649-86d1-4aa8-8ec2-d322b6a2c457
          HostingUnitName      : MyHostingUnit
          HypervisorConnection : MyConnection
          RootPath             : /
          RootId               :
          NetworkPath          : /Network 0.network
          NetworkId            : ab47080b-ca15-771a-c8dc-6ad9650158f1
          Storage              : {/Local storage.storage}
          PersonalvDiskStorage : {/Local storage.storage, /newStorage.storage}
          VMTaggingEnabled     : True
          AdditionalStorage    : {TemporaryStorage}
          Metadata             : {}
```
   Description<br>-----------<br>The command adds a new storage location called "newStorage.storage" to the hosting unit called "MyHostingUnit".
