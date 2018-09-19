# Get-ProvScheme

   Gets the list of provisioning schemes.

## Syntax
```
Get-ProvScheme [[-ProvisioningSchemeName] <String>] [-ProvisioningSchemeUid <Guid>] [-ScopeId <Guid>] [-ScopeName <String>] [-ReturnTotalRecordCount] [-MaxRecordCount <Int32>] [-Skip <Int32>] [-SortBy <String>] [-Filter <String>] [-AdminAddress <String>] [<CommonParameters>]
```

## Detailed Description
   Lets you retrieve the list of defined provisioning schemes.

## Related Commands
  * [New-ProvScheme](New-ProvScheme/)
  * [Remove-ProvScheme](Remove-ProvScheme/)
  * [Add-ProvSchemeMetadata](Add-ProvSchemeMetadata/)
  * [Remove-ProvSchemeMetadata](Remove-ProvSchemeMetadata/)
  * [Add-ProvSchemeControllerAddress](Add-ProvSchemeControllerAddress/)
  * [Remove-ProvSchemeControllerAddress](Remove-ProvSchemeControllerAddress/)
## Parameters

| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| ProvisioningSchemeName | The name of the provisioning scheme. | false | false |  |
| ProvisioningSchemeUid | The unique identifier of the provisioning scheme. | false | false |  |
| ScopeId | Gets only results with a scope matching the specified scope identifier. | false | false |  |
| ScopeName | Gets only results with a scope matching the specified scope name. | false | false |  |
| ReturnTotalRecordCount | See about_Prov_Filtering for details. | false | false | false |
| MaxRecordCount | See about_Prov_Filtering for details. | false | false | false |
| Skip | See about_Prov_Filtering for details. | false | false | 0 |
| SortBy | See about_Prov_Filtering for details. | false | false |  |
| Filter | See about_Prov_Filtering for details. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snap-in connects to.  You can provide this as a host name or an IP address. | false | false | LocalHost. When a value is provided by any cmdlet, this value becomes the default. |

## Input Type
### 
   
## Return Values

### Citrix.MachineCreation.Sdk.ProvisioningScheme<br>    

This object provides details of the provisioning scheme and contains the following information:<br>    ProvisioningSchemeUid <Guid><br>        The unique identifier for the provisioning scheme.<br>    ProvisioningSchemeName <string><br>        The name of the provisioning scheme.<br>    CpuCount <int><br>        The number of processors that VMs will be created with when using this scheme.<br>    MemoryMB <int><br>        The maximum amount of memory that VMs will be created with when using this scheme.<br>    MasterImageVM <string><br>        The path within the hosting unit provider to the copy of the VM snapshot that the scheme uses.<br>    MasterImageVMDate <DateTime><br>        The date and time that the copy was made of the VM snapshot used by the scheme.<br>    IdentityPoolUid <Guid><br>        The unique identifier of the identity pool (from the ADIdentity PowerShell snap-in) that the scheme uses.<br>    IdentityPoolName <string><br>        The name of the identity pool (from the ADIdentity PowerShell snap-in) that the scheme uses.<br>    HostingUnitUid <Guid><br>       The unique identifier of the hosting unit (from the Hosting Unit PowerShell snap-in) that the scheme uses.<br>    HostingUnitName <string><br>       The name of the hosting unit (from the Hosting Unit PowerShell snap-in) that the scheme uses.<br>    CleanOnBoot <Boolean><br>       Indicates whether the VMs that are created will be reset to a clean state on each boot.<br>    TaskId <Guid><br>       The identifier of any current task that is running for the provisioning scheme.<br>    Metadata <Citrix.MachineCreation.Sdk.Metadata[]><br>       The metadata associated with this provisioning scheme.<br>    ControllerAddress <string[]><br>       The DNS names of the controllers associated with this provisioning scheme for Quick Deploy purposes.<br>    VMMetadata <char[]><br>        The opaque VM metadata block<br>    UsePersonalVDiskStorage <bool><br>        True if the scheme will use personal vDisk storage.<br>    PersonalVDiskDriveLetter <char><br>        The drive letter for the personal vDisk<br>    PersonalVDiskDriveSize <int><br>        The size of the personal vDisk in GB<br>    ProfileUsagePercentage <double><br>        The percentage of the personal vDisk to be used for profile data<br>    DedicatedTenancy <bool><br>        Whether to use dedicated tenancy when creating machines in Cloud Hypervisors.<br>    CurrentMasterImageUid <Guid><br>        The unique identifier of the current master image used by the provisioning scheme. (See Get-ProvSchemeMasterVMImageHistory.)<br>    UseWriteBackCache <bool><br>        True if the scheme will use the write back cache feature.<br>    WriteBackCacheDiskSize <int><br>          The size of the write back cache disk if specified in GB.<br>    WriteBackCacheMemorySize <int><br>          The size of the write back memory cache if specified in MB.<br>    UseFullDiskCloneProvisioning <bool><br>          Indicates whether the machines are provisioned using the dedicated full disk clone feature.
   ## Notes
   In the case of failure, the following errors can result.<br>    Error Codes<br>    -----------<br>    PartialData<br>    Only a subset of the available data was returned.<br>    CouldNotQueryDatabase<br>    The query to get the database was not defined.<br>    PermissionDenied<br>    The user does not have administrative rights to perform this operation.<br>    ConfigurationLoggingError<br>    The operation could not be performed because of a configuration logging error.<br>    CommunicationError<br>    An error occurred while communicating with the service.<br>    DatabaseNotConfigured<br>    The operation could not be completed because the database for the service is not configured.<br>    InvalidFilter<br>    A filtering expression was supplied that could not be interpreted for this cmdlet.<br>    ExceptionThrown<br>    An unexpected error occurred.  To locate more details, see the Windows event logs on the controller being used, or examine the XenDesktop logs.
## Examples

### EXAMPLE 1
```
C:\PS>Get-ProvScheme


ProvisioningSchemeUid        : 7585f0de-192e-4847-a6d8-22713c3a2f42
ProvisioningSchemeName       : Scheme1
CpuCount                     : 1
MemoryMB                     : 1024
MasterImageVM                : /Base.vm/base.snapshot
MasterImageVMDate            : 17/05/2010 09:27:50
IdentityPoolUid              : 03743136-e43b-4a87-af74-ab71686b3c16
IdentityPoolName             : idPool1
HostingUnitUid               : 01a4a008-8ce8-4165-ba9c-cdf15a6b0501
HostingUnitName              : HostUnit1
CleanOnBoot                  : True
TaskId                       : 00000000-0000-0000-0000-000000000000
Metadata                     : {Department = Sales}
ControllerAddress            : {}
VMMetadata                   : {0, 1, 0, 0...}
PersonalVDiskDriveLetter     :
PersonalVDiskDriveSize       : 0
UsePersonalVDiskStorage      : False
NetworkMaps                  : {0}
Scopes                       :
DedicatedTenancy             : False
GpuTypeId                    :
ResetAdministratorPasswords  : False
SecurityGroups               : {}
ServiceOffering              :
CurrentMasterImageUid        : c0571690-4f57-4476-901b-fe64d6aecb79
UseWriteBackCache            : True
WriteBackCacheDiskSize       : 24
WriteBackCacheMemorySize     : 256
UseFullDiskCloneProvisioning : False

ProvisioningSchemeUid        : 43d82099-1fd7-4617-93f0-25b160813905
ProvisioningSchemeName       : Scheme2
CpuCount                     : 1
MemoryMB                     : 1024
MasterImageVM                : /Base.vm/base.snapshot
MasterImageVMDate            : 17/05/2010 09:53:40
IdentityPoolUid              : 03743136-e43b-4a87-af74-ab71686b3c16
IdentityPoolName             : idPool1
HostingUnitUid               : 01a4a008-8ce8-4165-ba9c-cdf15a6b0501
HostingUnitName              : HostUnit1
CleanOnBoot                  : True
TaskId                       : 00000000-0000-0000-0000-000000000000
Metadata                     : {}
ControllerAddress            : {}
VMMetadata                   : {0, 1, 0, 0...}
PersonalVDiskDriveLetter     :
PersonalVDiskDriveSize       : 0
UsePersonalVDiskStorage      : False
NetworkMaps                  : {0}
Scopes                       :
DedicatedTenancy             : False
GpuTypeId                    :
ResetAdministratorPasswords  : False
SecurityGroups               : {}
ServiceOffering              :
CurrentMasterImageUid        : 022cd6e4-34cb-3f7c-e02a-44ac404483b4
UseWriteBackCache            : True
WriteBackCacheDiskSize       : 24
WriteBackCacheMemorySize     : 256
UseFullDiskCloneProvisioning : False
```
   Description<br>-----------<br>Returns all of the available provisioning schemes.
### EXAMPLE 2
```
C:\PS>Get-ProvScheme -ProvisioningSchemeName Scheme[0-1]


ProvisioningSchemeUid        : 7585f0de-192e-4847-a6d8-22713c3a2f42
ProvisioningSchemeName       : Scheme1
CpuCount                     : 1
MemoryMB                     : 1024
MasterImageVM                : /Base.vm/base.snapshot
MasterImageVMDate            : 17/05/2010 09:27:50
IdentityPoolUid              : 03743136-e43b-4a87-af74-ab71686b3c16
IdentityPoolName             : idPool1
HostingUnitUid               : 01a4a008-8ce8-4165-ba9c-cdf15a6b0501
HostingUnitName              : HostUnit1
CleanOnBoot                  : True
TaskId                       : 00000000-0000-0000-0000-000000000000
Metadata                     : {}
ControllerAddress            : {}
VMMetadata                   : {0, 1, 0, 0...}
PersonalVDiskDriveLetter     :
PersonalVDiskDriveSize       : 0
UsePersonalVDiskStorage      : False
NetworkMaps                  : {0}
Scopes                       :
DedicatedTenancy             : False
GpuTypeId                    :
ResetAdministratorPasswords  : False
SecurityGroups               : {}
ServiceOffering              :
CurrentMasterImageUid        : c0571690-4f57-4476-901b-fe64d6aecb79
UseWriteBackCache            : True
WriteBackCacheDiskSize       : 24
WriteBackCacheMemorySize     : 256
UseFullDiskCloneProvisioning : False
```
   Description<br>-----------<br>Returns all of the provisioning schemes that have the name 'Scheme0' or 'Scheme1'.
