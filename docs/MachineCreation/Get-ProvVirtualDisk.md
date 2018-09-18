# Get-ProvVirtualDisk

   Gets any Virtual Disks that are known to the Machine Creation Service.

## Syntax
```
Get-ProvVirtualDisk [-VirtualDiskId <Guid>] [-StorageId <Guid>] [-HostingUnitUid <Guid>] [-ReturnTotalRecordCount] [-MaxRecordCount <Int32>] [-Skip <Int32>] [-SortBy <String>] [-Filter <String>] [-AdminAddress <String>] [<CommonParameters>]
```

## Detailed Description
   Provides the ability to obtain a list of the Virtual Disks that are known to the Machine Creation Service and their locations on the storage.

## Related Commands
  * [Get-ProvVirtualDiskPendingOperation](Get-ProvVirtualDiskPendingOperation/)
## Parameters

| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| VirtualDiskId | The identifier for the virtual disk. | false | true (ByPropertyName) |  |
| StorageId | The identifier for the storage location on which the virtual disk is located. | false | false |  |
| HostingUnitUid | The identifier for the hosting unit used for the provisioning scheme. | false | true (ByPropertyName) |  |
| ReturnTotalRecordCount | See about_Prov_Filtering for details. | false | false | false |
| MaxRecordCount | See about_Prov_Filtering for details. | false | false | false |
| Skip | See about_Prov_Filtering for details. | false | false | 0 |
| SortBy | See about_Prov_Filtering for details. | false | false |  |
| Filter | See about_Prov_Filtering for details. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snap-in connects to.  You can provide this as a host name or an IP address. | false | false | localhost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type
### 
   
## Return Values
### Citrix.MachineCreation.Sdk.VirtualDisk
   The object has the following properties:<br>VirtualDiskId <Guid><br>The unique identifier for the virtual disk<br>HostingUnitUid <Guid><br>The unique identifier for the hosting unit<br>VirtualDiskType <string><br>A value indicating the type of the virtual disk (e.g. AppDisk)<br>VirtualDiskLocations <Citrix.MachineCreation.Sdk.VirtualDiskLocation><br>An array of objects, with each giving the location of the virtual disk on a storage location of the hosting unit<br>AllowAutomaticReplication <bool><br>A value indicating whether the virtual disk will be replicated automatically to all storage locations defined within the hosting unit## Notes
   In the case of failure, the following errors can result.<br>    Error Codes<br>    -----------<br>    PartialData<br>    Only a subset of the available data was returned.<br>    CouldNotQueryDatabase<br>    The query required to get the database was not defined.<br>    PermissionDenied<br>    The user does not have administrative rights to perform this operation.<br>    ConfigurationLoggingError<br>    The operation could not be performed because of a configuration logging error<br>    CommunicationError<br>    An error occurred while communicating with the service.<br>    DatabaseNotConfigured<br>    The operation could not be completed because the database for the service is not configured.<br>    InvalidFilter<br>    A filtering expression was supplied that could not be interpreted for this cmdlet.<br>    ExceptionThrown<br>    An unexpected error occurred.  To locate more details, see the Windows event logs on the controller being used or examine the XenDesktop logs.
## Examples

### EXAMPLE 1
```
PS C:\> Get-ProvVirtualDisk

          AllowAutomaticReplication : False
          HighPriority              : False
          HostingUnitUid            : e22036f7-1026-467e-a8af-fad81f8eddf8
          VirtualDiskId             : 51a55b3a-a713-4692-ae57-15aa0c050486
          VirtualDiskLocations      : {a0788335-c0d6-428c-8168-fad6bdb48010}
          VirtualDiskType           : ControlDisk

          AllowAutomaticReplication : True
          HighPriority              : False
          HostingUnitUid            : e22036f7-1026-467e-a8af-fad81f8eddf8
          VirtualDiskId             : 2677e07f-b53d-4b4b-afbb-94af6461b9b1
          VirtualDiskLocations      : {21cd1a35-a5b9-4c86-81f8-f90d0c76b352}
          VirtualDiskType           : AppDisk

          AllowAutomaticReplication : False
          HighPriority              : False
          HostingUnitUid            : 98636b1f-eab8-419f-80ce-8e41740bc251
          VirtualDiskId             : 1b213058-f33c-40bb-85e9-b4a3cc5cb1de
          VirtualDiskLocations      : {Version=2,LsiLogicScsi,-1,,[Shared] AppDisk-VirtualDiskId-1b213058-f33c-40bb-85e9-b4a3cc5cb1de/01 Jan 2016 00-01-02.9567Z.vmdk,resgroup-116,Vmfs}
          VirtualDiskType           : AppDisk
```
   Description<br>-----------<br>Gets all virtual disks known to MCS.
### EXAMPLE 2
```
PS C:\> Get-ProvVirtualDisk -HostingUnitUid e22036f7-1026-467e-a8af-fad81f8eddf8

          AllowAutomaticReplication : False
          HighPriority              : False
          HostingUnitUid            : e22036f7-1026-467e-a8af-fad81f8eddf8
          VirtualDiskId             : 51a55b3a-a713-4692-ae57-15aa0c050486
          VirtualDiskLocations      : {a0788335-c0d6-428c-8168-fad6bdb48010}
          VirtualDiskType           : ControlDisk

          AllowAutomaticReplication : True
          HighPriority              : False
          HostingUnitUid            : e22036f7-1026-467e-a8af-fad81f8eddf8
          VirtualDiskId             : 2677e07f-b53d-4b4b-afbb-94af6461b9b1
          VirtualDiskLocations      : {21cd1a35-a5b9-4c86-81f8-f90d0c76b352}
          VirtualDiskType           : AppDisk
```
   Description<br>-----------<br>Gets all virtual disks associated with the given hosting unit.
