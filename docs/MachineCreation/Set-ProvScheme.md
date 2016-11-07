# Set-ProvScheme

   Changes the parameter values for a provisioning scheme.

## Syntax
```
Set-ProvScheme [-ProvisioningSchemeName] <String> [-VMCpuCount <Int32>] [-VMMemoryMB <Int32>] [-CustomProperties <String>] [-ServiceOffering <String>] [-PassThru] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]

Set-ProvScheme [-ProvisioningSchemeName] <String> -IdentityPoolName <String> [-VMCpuCount <Int32>] [-VMMemoryMB <Int32>] [-CustomProperties <String>] [-ServiceOffering <String>] [-PassThru] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]

Set-ProvScheme [-ProvisioningSchemeName] <String> -IdentityPoolUid <Guid> [-VMCpuCount <Int32>] [-VMMemoryMB <Int32>] [-CustomProperties <String>] [-ServiceOffering <String>] [-PassThru] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]

Set-ProvScheme -ProvisioningSchemeUid <Guid> [-VMCpuCount <Int32>] [-VMMemoryMB <Int32>] [-CustomProperties <String>] [-ServiceOffering <String>] [-PassThru] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]

Set-ProvScheme -ProvisioningSchemeUid <Guid> -IdentityPoolName <String> [-VMCpuCount <Int32>] [-VMMemoryMB <Int32>] [-CustomProperties <String>] [-ServiceOffering <String>] [-PassThru] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]

Set-ProvScheme -ProvisioningSchemeUid <Guid> -IdentityPoolUid <Guid> [-VMCpuCount <Int32>] [-VMMemoryMB <Int32>] [-CustomProperties <String>] [-ServiceOffering <String>] [-PassThru] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
```

## Detailed Description
   Provides the ability to update the parameters of an existing provisioning scheme.

This allows the following parameters to be updated:

Number of CPUs that will be used for VMs created from the provisioning scheme. Maximum amount of memory that will be used for VMs created from the provisioning scheme.

To change the name of the provisioning scheme see Rename-ProvScheme.

## Related Commands
  * [New-ProvScheme](New-ProvScheme.html)
  * [Remove-ProvScheme](Remove-ProvScheme.html)
  * [Get-ProvScheme](Get-ProvScheme.html)
  * [Rename-ProvScheme](Rename-ProvScheme.html)
## Parameters

| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| ProvisioningSchemeName | The name of the provisioning scheme to be updated. | true | false |  |
| IdentityPoolName | The name of an identity pool to associate with the provisioning scheme, replacing the present one. | true | false |  |
| IdentityPoolUid | The identifier of an identity pool to associate with the provisioning scheme, replacing the present one. | true | false |  |
| ProvisioningSchemeUid | The identifier of the provisioning scheme to be updated. | true | false |  |
| VMCpuCount | The number of processors that virtual machines created from the provisioning scheme should use. | false | false |  |
| VMMemoryMB | The maximum amount of memory that virtual machines created from the provisioning scheme should use. | false | false |  |
| CustomProperties | The properties of the provisioning scheme that are specific to the target hosting infrastructure. | false | false |  |
| ServiceOffering | The name of the cloud service offering to use when creating machines. | false | false |  |
| PassThru | Returns the affected record. By default, this cmdlet does not generate any output. | false | false | False |
| LoggingId | Specifies the identifier of the high-level operation this cmdlet call forms a part of. Citrix Studio and Director typically create high-level operations. PowerShell scripts can also wrap a series of cmdlet calls in a high-level operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller the PowerShell snap-in will connect to. You can provide this as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type
### 
   
## Return Values
### Citrix.MachineCreation.Sdk.ProvisioningScheme<br>    This object provides details of the provisioning scheme and contains the following information:<br>    ProvisioningSchemeUid<br>    ProvisioningSchemeName<br>        The name of the provisioning scheme.<br>    CpuCount<br>        The numer of processors that VMs will be created with when using this scheme.<br>    MemoryMB<br>        The maximum amount of memory that VMs will be created with when using this scheme.<br>    MasterImageVM<br>        The path within the hosting unit provider to the VM or snapshot of which the scheme is currently using a copy.<br>    MasterImageVMDate<br>        The date and time that the copy of the VM image was made for the scheme.<br>    IdentityPoolUid<br>        The unique identifier of the identity pool (from the ADIdentity PowerShell snap-in) that the scheme uses.<br>    IdentityPoolName<br>        The name of the identity pool (from the ADIdentity PowerShell snap-in) that the scheme uses.<br>    HostingUnitUid<br>       The unique identifier of the hosting unit (from the Hosting Unit PowerShell snap-in) that the new provisioning scheme will use.<br>    HostingUnitName<br>       The name of the hosting unit (from the Hosting Unit PowerShell snap-in) that the new provisioning scheme will use.<br>    CleanOnBoot<br>       Indicates whether the VMs created are to be reset to a clean state on each boot.<br>    TaskId<br>       The identifier of any current task that is running for the provisioning scheme.
   ## Notes
   In the case of failure, the following errors can result.<br>    Error Codes<br>    -----------<br>    ProvisioningSchemeNotFound<br>    The specified provisioning scheme could not be located.<br>    DatabaseError<br>    An error occurred in the service while attempting a database operation.<br>    DatabaseNotConfigured<br>    The operation could not be completed because the database for the service is not configured.<br>    ServiceStatusInvalidDb<br>    An error occurred in the service while attempting a database operation - communication with the database failed for<br>    for various reasons.<br>    CommunicationError<br>    An error occurred while communicating with the service.<br>    PermissionDenied<br>    The user does not have administrative rights to perform this operation.<br>    ConfigurationLoggingError<br>    The operation could not be performed because of a configuration logging error<br>    HostingUnitNotFound<br>    The hosting unit referenced by the provisioning scheme could not be resolved<br>    ExceptionThrown<br>    An unexpected error occurred.  To locate more details, see the Windows event logs on the controller being used or examine the XenDesktop logs.
## Examples

### EXAMPLE 1
```
C:\PS> Set-ProvScheme -ProvisioningSchemeName MyScheme -VMCpuCount 2
```
   Description<br>-----------<br>Updates a provisioning scheme called "MyScheme" to use two processors on the VMs that are created from the provisioning scheme.
