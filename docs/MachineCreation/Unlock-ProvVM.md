# Unlock-ProvVM

   Unlocks a VM.

## Syntax
```
Unlock-ProvVM [-VMID] <String[]> -ProvisioningSchemeName <String> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]

Unlock-ProvVM [-VMID] <String[]> -ProvisioningSchemeUid <Guid> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
```

## Detailed Description
   Provides the ability to unlock a virtual machine.

## Related Commands
  * [Get-ProvVM](Get-ProvVM/)
  * [Lock-ProvVM](Lock-ProvVM/)
## Parameters

| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| VMID | The virtual machine Id (hypervisor context) | true | true (ByPropertyName) |  |
| ProvisioningSchemeName | The name of the provisioning scheme. | true | true (ByPropertyName) |  |
| ProvisioningSchemeUid | The unique identifier of the provisioning scheme. | true | false |  |
| LoggingId | Specifies the identifier of the high-level operation this cmdlet call forms a part of. Citrix Studio and Director typically create high-level operations. PowerShell scripts can also wrap a series of cmdlet calls in a high-level operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snap-in connects to.  You can provide this as a host name or an IP address. | false | false | LocalHost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type
### Citrix.MachineCreation.Sdk.ProvisionedVirtualMachine<br>    You can pipe an object containing a parameter called 'VMId' and 'ProvisioningSchemeName' to Lock-ProvVM
   
## Return Values
### 
   ## Notes
   In the case of failure, the following errors can result.<br>    Error Codes<br>    -----------<br>    VMDoesNotExist<br>    The specified VM cannot be located.<br>    VMAlreadyUnLocked<br>    The VM is already unlocked.<br>    VMDoesNotExistForProvisioningScheme<br>    The specified VM does exist in the hypervisor, but is not part of the specified provisioning scheme.<br>    DatabaseError<br>    An error occurred in the service while attempting a database operation.<br>    DatabaseNotConfigured<br>    The operation could not be completed because the database for the service is not configured.<br>    ServiceStatusInvalidDb<br>    An error occurred in the service while attempting a database operation - communication with the database failed for<br>    for various reasons.<br>    CommunicationError<br>    An error occurred while communicating with the service.<br>    PermissionDenied<br>    The user does not have administrative rights to perform this operation.<br>    ConfigurationLoggingError<br>    The operation could not be performed because of a configuration logging error<br>    ExceptionThrown<br>    An unexpected error occurred.  To locate more details, see the Windows event logs on the controller being used or examine the XenDesktop logs.
## Examples

### EXAMPLE 1
```
C:\PS>Unlock-ProvVM -provisioningSchemeName MyScheme -VMId  bc79802c-ba6e-8de8-99e9-4c35d7ad24b4
```
   Description<br>-----------<br>Unlocks the VM with the Id 'bc79802c-ba6e-8de8-99e9-4c35d7ad24b4' in the provisioning scheme 'MyScheme'.
### EXAMPLE 2
```
C:\PS>Get-ProvVM -provisioningSchemeName MyScheme | Unlock-ProvVM
```
   Description<br>-----------<br>Unlocks all the VMs in the provisioning scheme 'MyScheme'.
### EXAMPLE 3
```
C:\PS>Get-ProvVM -Locked $True | Unlock-ProvVM
```
   Description<br>-----------<br>Unlocks all the VMs that are currently locked.
