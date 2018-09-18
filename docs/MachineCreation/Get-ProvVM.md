# Get-ProvVM

   Gets the VMs that were created using Citrix XenDesktop Machine Creation Services.

## Syntax
```
Get-ProvVM [[-ProvisioningSchemeName] <String>] [-ProvisioningSchemeUid <Guid>] [-VMName <String>] [-Locked <Boolean>] [-Tag <String>] [-OutOfDate] [-ReturnTotalRecordCount] [-MaxRecordCount <Int32>] [-Skip <Int32>] [-SortBy <String>] [-Filter <String>] [-AdminAddress <String>] [<CommonParameters>]
```

## Detailed Description
   Provides the ability to obtain a list of the VMs that were created using Machine Creation Services.

## Related Commands
  * [New-ProvVM](New-ProvVM/)
  * [Remove-ProvVM](Remove-ProvVM/)
  * [Lock-ProvVM](Lock-ProvVM/)
  * [Unlock-ProvVM](Unlock-ProvVM/)
## Parameters

| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| ProvisioningSchemeName | The name of the provisioning scheme. | false | false |  |
| ProvisioningSchemeUid | The unique identifier of the provisioning scheme. | false | false |  |
| VMName | The name of the VM in the hypervisor context. | false | false |  |
| Locked | Indicates whether only VMs that are marked as locked are returned or not (see Lock-ProvVM and Unlock-ProvVM for details). | false | false |  |
| Tag | The tag string that was associated with the VM when it was locked. | false | false |  |
| OutOfDate | Indicates that the image currently assigned to the VM is out of date.  The image will be updated the next time the VM is restarted. | false | false |  |
| ReturnTotalRecordCount | See about_Prov_Filtering for details. | false | false | false |
| MaxRecordCount | See about_Prov_Filtering for details. | false | false | false |
| Skip | See about_Prov_Filtering for details. | false | false | 0 |
| SortBy | See about_Prov_Filtering for details. | false | false |  |
| Filter | See about_Prov_Filtering for details. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snap-in connects to.  You can provide this as a host name or an IP address. | false | false | LocalHost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type
### 
   
## Return Values
### Citrix.MachineCreation.Sdk.ProvisionedVirtualMachine<br>   The object has the following properties:<br>   ADAccountSid <string><br>       The SID of the AD computer account that the VM is using.<br>   ADAccountName <string><br>       The name of the AD computer account that the VM is using.<br>   CpuCount <int><br>       The number of processors that the VM has been allocated.<br>   CreationDate <DateTime><br>       The date and time that the VM was created.<br>   Domain <string><br>       The Domain of the AD computer account that the VM is using.<br>   ImageOutOfDate <Boolean><br>       Indicates if the image will be updated next time the VM is started.<br>   Lock <Boolean><br>       Indicates whether the VM is locked or not.<br>   MemoryMB <int><br>       The maximum amount of memory that VMs will be created with when using this scheme.<br>   ProvisioningSchemeName <string><br>       The name of the provisioning scheme that the VM is part of.<br>   ProvisioningSchemeUid <Guid><br>       The unique identifier for the provisioning scheme that the VM is part of.<br>   Tag <string><br>       Provides the string associated with a locked VM.<br>   VMId <string><br>       The identifier for the VM (hypervisor context).<br>   VMName <string><br>       The name of the VM (hypervisor context).<br>   AssignedImage <string><br>       The identifier (in the hypervisor) for the hard disk image that the VM is currently assigned.<br>   BootedImage <string><br>       The identifier (in the hypervisor) for the hard disk image with which the VM is currently started.<br>   HostingUnitUid <Guid><br>       The unique identifier for the hosting unit that was used to create the VM.<br>   HypervisorConnectionUid <Guid><br>       The unique identifier of the hypervisor connection that was used to create the VM.<br>   LastBootTime <DateTime><br>       The date and time of the last start of the VM.<br>   OSDiskIndex <int><br>       The disk index at which the hard disk image, from which the VM is currently started, is attached (or [int]::MinValue for VMs inherited from versions of XenDesktop before 5.6)<br>   PersonalVDiskIndex <int><br>       The disk index at which the personal vdisk is attached (defaults to [int]::MinValue for VMs without a personal vdisk)<br>   PersonalVDiskStorage <string><br>       The identifier (in the hypervisor) for the storage on which the personal virtual disk image from which the VM is currently started is located.  This is set only if the VM has a personal vDisk attached<br>   StorageId <string><br>       The identifier (in the hypervisor) for the storage on which the hard disk image, from which the VM is currently started, is located.
   ## Notes
   In the case of failure, the following errors can result.<br>    Error Codes<br>    -----------<br>    PartialData<br>    Only a subset of the available data was returned.<br>    CouldNotQueryDatabase<br>    The query required to get the database was not defined.<br>    PermissionDenied<br>    The user does not have administrative rights to perform this operation.<br>    ConfigurationLoggingError<br>    The operation could not be performed because of a configuration logging error<br>    CommunicationError<br>    An error occurred while communicating with the service.<br>    DatabaseNotConfigured<br>    The operation could not be completed because the database for the service is not configured.<br>    InvalidFilter<br>    A filtering expression was supplied that could not be interpreted for this cmdlet.<br>    ExceptionThrown<br>    An unexpected error occurred.  To locate more details, see the Windows event logs on the controller being used or examine the XenDesktop logs.
## Examples

### EXAMPLE 1
```
C:\PS>Get-ProvVM -provisioningSchemeName MyScheme

ADAccountName           : MYDomain\computer2$
ADAccountSid            : S-1-5-21-3751941309-1176885247-1409628468-3179
CpuCount                : 1
CreationDate            : 17/05/2012 09:35:22
Domain                  : steve.dum.local
ImageOutOfDate          : False
Lock                    : True
MemoryMB                : 512
ProvisioningSchemeName  : XenPS
ProvisioningSchemeUid   : 5135a865-ba49-4e5f-87f2-2d65ee7a4e51
Tag                     : Brokered
VMId                    : a830de93-ddc5-b763-dc1a-35580a31401c
VMName                  : IP0051
AssignedImage           : 57fc60c3-eb9b-4d38-8646-0afceec85335
BootedImage             : 57fc60c3-eb9b-4d38-8646-0afceec85335
HostingUnitUid          : ea17840f-cf2d-4d80-94e0-3b752b32e0af
HypervisorConnectionUid : 99f9f826-31fc-4453-8ca0-9ba54306c3ac
IdentityDiskIndex       : 1
LastBootTime            : 17/05/2012 09:35:22
OSDiskIndex             : 0
PersonalVDiskIndex      : -2147483648
PersonalVDiskStorage    : 
StorageId               : 33ad07a7-edd7-589b-716a-86cad4739f5e
```
   Description<br>-----------<br>Gets all the Virtual Machines that were provisioned into the Provisioning Scheme called 'MyScheme'.
### EXAMPLE 2
```
C:\PS>Get-ProvVM -Locked $true
        
ADAccountName           : MYDomain\computer1$
ADAccountSid            : S-1-5-21-3751941309-1176885247-1409628468-3178
CpuCount                : 1
CreationDate            : 17/05/2012 09:35:30
Domain                  : steve.dum.local
ImageOutOfDate          : False
Lock                    : True
MemoryMB                : 512
ProvisioningSchemeName  : XenPS
ProvisioningSchemeUid   : 5135a865-ba49-4e5f-87f2-2d65ee7a4e51
Tag                     : Brokered
VMId                    : a830de93-ddc5-b763-dc1a-35580a31401c
VMName                  : IP0051
AssignedImage           : 57fc60c3-eb9b-4d38-8646-0afceec85335
BootedImage             : 57fc60c3-eb9b-4d38-8646-0afceec85335
HostingUnitUid          : ea17840f-cf2d-4d80-94e0-3b752b32e0af
HypervisorConnectionUid : 99f9f826-31fc-4453-8ca0-9ba54306c3ac
IdentityDiskIndex       : 1
LastBootTime            : 17/05/2012 09:35:22
OSDiskIndex             : 0
PersonalVDiskIndex      : -2147483648
PersonalVDiskStorage    : 
StorageId               : 33ad07a7-edd7-589b-716a-86cad4739f5e
```
   Description<br>-----------<br>Gets all the Virtual Machines that were locked, regardless of which Provisioning Scheme the VM is part of.
