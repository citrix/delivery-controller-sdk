# Remove-ProvScheme

   Removes a provisioning scheme

## Syntax
```
Remove-ProvScheme [-ProvisioningSchemeName] <String> [-ForgetVM] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]

Remove-ProvScheme -ProvisioningSchemeUid <Guid> [-ForgetVM] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
```

## Detailed Description
   Provides the ability to remove a provisioning Scheme.  The provisioning scheme must not contain any VMs unless the 'ForgetVM' option is specified.

If 'ForgetVM' is not specified, a cmdlet task is created that runs in the background to remove the hard disk copies that have been created for the provisioning scheme in hypervisor storage.  Use the Get-ProvTask command to monitor the progress of this task.

## Related Commands
  * [Get-ProvTask](Get-ProvTask.html)
  * [New-ProvScheme](New-ProvScheme.html)
## Parameters

| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| ProvisioningSchemeName | The name of the provisioning scheme to be removed. | true | true (ByPropertyName) |  |
| ProvisioningSchemeUid | The unique identifier for the provisioning scheme to be removed. | true | true (ByPropertyName) |  |
| ForgetVM | Indicates whether or not the VMs in the provisioning scheme should be left in the hypervisor and only the data held in the Machine Creation Services removed.  If this is specified, it is up to the administrator of the hypervisor to remove the VMs and hard disk images using the tools provided by the hypervisor itself. | false | false |  |
| LoggingId | Specifies the identifier of the high-level operation this cmdlet call forms a part of. Citrix Studio and Director typically create high-level operations. PowerShell scripts can also wrap a series of cmdlet calls in a high-level operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snap-in connects to.  You can provide this as a host name or an IP address. | false | false | LocalHost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type
### 
   
## Return Values
### Citrix.MachineCreation.Sdk.ProvisioningScheme<br>    This object provides details of the provisioning scheme and contains the following information:<br>    ProvisioningSchemeUid<br>        The unique identifier for the provisioning scheme.<br>    ProvisioningSchemeName<br>        The name of the provisioning scheme.<br>    CpuCount<br>        The number of processors that VMs will be created with when using this scheme.<br>    MemoryMB<br>        The maximum amount of memory that VMs will be created with when using this scheme.<br>    MasterImageVM<br>        The path within the hosting unit provider to the VM or snapshot of which the scheme is currently using a copy.<br>    MasterImageVMDate<br>        The date and time that the copy of the VM image was made for the scheme.<br>    IdentityPoolUid<br>        The unique identifier of the identity pool (from the ADIdentity PowerShell snap-in) that the scheme uses.<br>    IdentityPoolName<br>        The name of the identity pool (from the ADIdentity PowerShell snap-in) that the scheme uses.<br>    HostingUnitUid<br>       The unique identifier of the hosting unit (from the Hosting Unit PowerShell snap-in) that the new provisioning scheme will use.<br>    HostingUnitName<br>       The name of the hosting unit (from the hosting unit PowerShell snap-in) that the new provisioning scheme will use.<br>    CleanOnBoot<br>       Indicates whether the VMs created are to be reset to a clean state on each boot.<br>    TaskId<br>       The identifier of any current task that is running for the provisioning scheme.
   ## Notes
   If the hosting unit referenced by the provisioning scheme no longer exists (i.e. it has been removed using the Hosting Unit PowerShell snap-in), the provisioning scheme data is deleted from the database without errors. However, the hard disks associated with the provisioning scheme cannot be removed and remain in the hypervisor.<br>    In the case of failure, the following errors can result.<br>    Error Codes<br>    -----------<br>    IllegalParameter<br>    One or more parameters are illegal or are not specified.<br>    ProvisioningSchemeNotFound<br>    The specified provisioning scheme could not be located.<br>    UnableToRemoveProvisioningSchemeDueToAssociatedVM<br>    The provisioning scheme contained VMs and the 'ForgetVM' parameter was not specified.<br>    DatabaseError<br>    An error occurred in the service while attempting a database operation.<br>    DatabaseNotConfigured<br>    The operation could not be completed because the database for the service is not configured.<br>    ServiceStatusInvalidDb<br>    An error occurred in the service while attempting a database operation - communication with the database failed for<br>    for various reasons.<br>    CommunicationError<br>    An error occurred while communicating with the service.<br>    PermissionDenied<br>    The user does not have administrative rights to perform this operation.<br>    ConfigurationLoggingError<br>    The operation could not be performed because of a configuration logging error<br>    ExceptionThrown<br>    An unexpected error occurred.  To locate more details, see the Windows event logs on the controller being used or examine the XenDesktop logs.<br>    The cmdlet is associated with a task of type DisusedImageCleanUp, and while active will move through the following operations (CurrentOperation field)<br>    Running
## Examples

### EXAMPLE 1
```
c:\PS>Remove-ProvScheme -ProvisioningSchemeName $provScheme.ProvisioningSchemeName
```
   Description<br>-----------<br>Remove the empty provisioning scheme by name.
