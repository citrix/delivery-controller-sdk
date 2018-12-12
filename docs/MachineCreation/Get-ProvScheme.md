
# Get-Provscheme
Gets the list of provisioning schemes.
## Syntax
```
Get-ProvScheme [[-ProvisioningSchemeName] <String>] [-ProvisioningSchemeUid <Guid>] [-ScopeId <Guid>] [-ScopeName <String>] [-ReturnTotalRecordCount] [-MaxRecordCount <Int32>] [-Skip <Int32>] [-SortBy <String>] [-Filter <String>] [-BearerToken <String>] [-AdminAddress <String>] [<CommonParameters>]
```
## Detailed Description
Lets you retrieve the list of defined provisioning schemes.


## Related Commands

* [New-ProvScheme](./New-ProvScheme/)
* [Remove-ProvScheme](./Remove-ProvScheme/)
* [Add-ProvSchemeMetadata](./Add-ProvSchemeMetadata/)
* [Remove-ProvSchemeMetadata](./Remove-ProvSchemeMetadata/)
* [Add-ProvSchemeControllerAddress](./Add-ProvSchemeControllerAddress/)
* [Remove-ProvSchemeControllerAddress](./Remove-ProvSchemeControllerAddress/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| ProvisioningSchemeName | The name of the provisioning scheme. | false | false |  |
| ProvisioningSchemeUid | The unique identifier of the provisioning scheme. | false | false |  |
| ScopeId | Gets only results with a scope matching the specified scope identifier. | false | false |  |
| ScopeName | Gets only results with a scope matching the specified scope name. | false | false |  |
| ReturnTotalRecordCount | See about\_Prov\_Filtering for details. | false | false | false |
| MaxRecordCount | See about\_Prov\_Filtering for details. | false | false | false |
| Skip | See about\_Prov\_Filtering for details. | false | false | 0 |
| SortBy | See about\_Prov\_Filtering for details. | false | false |  |
| Filter | See about\_Prov\_Filtering for details. | false | false |  |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snap-in connects to.  You can provide this as a host name or an IP address. | false | false | LocalHost. When a value is provided by any cmdlet, this value becomes the default. |

## Input Type

### 

## Return Values

### Citrix.Machinecreation.Sdk.Provisioningscheme
This object provides details of the provisioning scheme and contains the following information:<br>    ProvisioningSchemeUid &lt;Guid&gt;<br>        The unique identifier for the provisioning scheme.<br>    ProvisioningSchemeName &lt;string&gt;<br>        The name of the provisioning scheme.<br>    CpuCount &lt;int&gt;<br>        The number of processors that VMs will be created with when using this scheme.<br>    MemoryMB &lt;int&gt;<br>        The maximum amount of memory that VMs will be created with when using this scheme.<br>    MasterImageVM &lt;string&gt;<br>        The path within the hosting unit provider to the copy of the VM snapshot that the scheme uses.<br>    MasterImageVMDate &lt;DateTime&gt;<br>        The date and time that the copy was made of the VM snapshot used by the scheme.<br>    IdentityPoolUid &lt;Guid&gt;<br>        The unique identifier of the identity pool (from the ADIdentity PowerShell snap-in) that the scheme uses.<br>    IdentityPoolName &lt;string&gt;<br>        The name of the identity pool (from the ADIdentity PowerShell snap-in) that the scheme uses.<br>    HostingUnitUid &lt;Guid&gt;<br>       The unique identifier of the hosting unit (from the Hosting Unit PowerShell snap-in) that the scheme uses.<br>    HostingUnitName &lt;string&gt;<br>       The name of the hosting unit (from the Hosting Unit PowerShell snap-in) that the scheme uses.<br>    CleanOnBoot &lt;Boolean&gt;<br>       Indicates whether the VMs that are created will be reset to a clean state on each boot.<br>    TaskId &lt;Guid&gt;<br>       The identifier of any current task that is running for the provisioning scheme.<br>    Metadata &lt;Citrix.MachineCreation.Sdk.Metadata\[\]&gt;<br>       The metadata associated with this provisioning scheme.<br>    ControllerAddress &lt;string\[\]&gt;<br>       The DNS names of the controllers associated with this provisioning scheme for Quick Deploy purposes.<br>    VMMetadata &lt;char\[\]&gt;<br>        The opaque VM metadata block<br>    UsePersonalVDiskStorage &lt;bool&gt;<br>        True if the scheme will use personal vDisk storage.<br>    PersonalVDiskDriveLetter &lt;char&gt;<br>        The drive letter for the personal vDisk<br>    PersonalVDiskDriveSize &lt;int&gt;<br>        The size of the personal vDisk in GB<br>    ProfileUsagePercentage &lt;double&gt;<br>        The percentage of the personal vDisk to be used for profile data<br>    DedicatedTenancy &lt;bool&gt;<br>        Whether to use dedicated tenancy when creating machines in Cloud Hypervisors.<br>    CurrentMasterImageUid &lt;Guid&gt;<br>        The unique identifier of the current master image used by the provisioning scheme. (See Get-ProvSchemeMasterVMImageHistory.)<br>    UseWriteBackCache &lt;bool&gt;<br>        True if the scheme will use the wrote back cache feature.<br>    WriteBackCacheDiskSize &lt;int&gt;<br>          The size of the write back cache disk if specified in GB.<br>    WriteBackCacheMemorySize &lt;int&gt;<br>          The size of the write back memory cache if specified in MB.<br>    UseFullDiskCloneProvisioning &lt;bool&gt;<br>          Indicates whether the machines are provisioned using the dedicated full disk clone feature.
## Notes
In the case of failure, the following errors can result.<br>    Error Codes<br>    -----------<br>    PartialData<br>    Only a subset of the available data was returned.<br>    CouldNotQueryDatabase<br>    The query to get the database was not defined.<br>    PermissionDenied<br>    The user does not have administrative rights to perform this operation.<br>    ConfigurationLoggingError<br>    The operation could not be performed because of a configuration logging error.<br>    CommunicationError<br>    An error occurred while communicating with the service.<br>    DatabaseNotConfigured<br>    The operation could not be completed because the database for the service is not configured.<br>    InvalidFilter<br>    A filtering expression was supplied that could not be interpreted for this cmdlet.<br>    ExceptionThrown<br>    An unexpected error occurred.  To locate more details, see the Windows event logs on the controller being used, or examine the XenDesktop logs.
## Examples

### Example 1
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
#### Description
Returns all of the available provisioning schemes.
### Example 2
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
#### Description
Returns all of the provisioning schemes that have the name 'Scheme0' or 'Scheme1'.
