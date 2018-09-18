# Remove-ProvVM

   Removes virtual machines.

## Syntax
```
Remove-ProvVM [-ProvisioningSchemeName] <String> -VMName <String[]> [-ForgetVM] [-RunAsynchronously] [-PurgeJobOnSuccess] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]

Remove-ProvVM [-ProvisioningSchemeUid] <Guid> -VMName <String[]> [-ForgetVM] [-RunAsynchronously] [-PurgeJobOnSuccess] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
```

## Detailed Description
   Lets you remove VMs from the Machine Creation Services and the hypervisor that they run on.

## Related Commands
  * [Get-ProvVM](Get-ProvVM/)
  * [New-ProvVM](New-ProvVM/)
## Parameters

| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| ProvisioningSchemeName | The name of the provisioning scheme from which virtual machines will be removed. | true | true (ByPropertyName) |  |
| ProvisioningSchemeUid | The unique identifier for the provisioning scheme from which the virtual machines are removed. | true | true (ByPropertyName) |  |
| VMName | List of VM names that will be removed from the provisioning scheme. | true | true (ByValue, ByPropertyName) |  |
| ForgetVM | The named VMs will only be removed from the provisioning scheme database, but will remain in the hypervisor. | false | false |  |
| RunAsynchronously | Indicates whether or not the command returns before it is complete. If this is specified, the command returns an identifier for the task that was created. This task can be monitored using the get-ProvTask command. | false | false | false |
| PurgeJobOnSuccess | Indicates that the task history is removed from the database when the task finishes. This cannot be specified for tasks that are run asynchronously. | false | false |  |
| LoggingId | Specifies the identifier of the high-level operation this cmdlet call forms a part of. Citrix Studio and Director typically create high-level operations. PowerShell scripts can also wrap a series of cmdlet calls in a high-level operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snap-in connects to. You can provide this as a host name or an IP address. | false | false | LocalHost. When a value is provided by any cmdlet, this value becomes the default. |

## Input Type
### 
   
## Return Values
### System.Guid<br>    When the RunAsynchronously identifier is specified, this GUID is returned and provides the task identifier.<br>System.Management.Automation.PSCustomObject<br>    This object provides details of the task that was run and contains the following information:<br>        TaskId <Guid><br>            The identifier for the task that was performed.<br>        Active <Boolean><br>            Indicates whether the task is still processing or is complete.<br>        Host <string><br>            The name of the host on which the task is running or was run.<br>        DateStarted <DateTime><br>            The date and time that the task was initiated.<br>        Type <Citrix.XDInterServiceTypes.JobType><br>            The type of task. For new remove-VM tasks, this is always "RemoveVirtualMachine".<br>        Metadata <Citrix.MachineCreation.Sdk.Metadata[]><br>            The list of metadata stored for the task. For new tasks, this is empty until metadata is added.<br>        WorkflowStatus <System.Workflow.Runtime.WorkflowStatus><br>            Indicates the status of the workflow that is used to process the task.<br>        ProvisioningSchemeName <string><br>            The name of the provisioning scheme that the task is for.<br>        ProvisioningSchemeUid <Guid><br>            The unique identifier of the provisioning scheme that the task is for.<br>        TaskState <Citrix.DesktopUpdateManager.SDK.ProvisionVMState><br>            The state of the task.  This can be any of the following:<br>            Processing<br>                Indicates that the task is in its initial state.<br>            LocatingResources,<br>                Indicates that the task is locating information from other services.<br>            HostingUnitNotFound<br>                Indicates that the required hosting unit could not be located.<br>            ProvisioningSchemeNotFound<br>                Indicates that the required provisioning scheme could not be located.<br>            Provisioning<br>                Indicates that the task is at the provisioning stage.<br>            IdentityPoolNotFound<br>                Indicates that the required identity pool could not be located.<br>            TaskAlreadyRunningForProvisioningScheme<br>                Indicates that the provisioning scheme already has another task running.<br>            Finalizing<br>                Indicates that the task is finalizing.<br>            Finished<br>                Indicates that the task is complete.<br>            FinishedWithErrors<br>                Indicates that the task is complete but there were errors. Specific details of errors are included with each failed virtual machine.<br>            Removing<br>                Indicates that the task is removing virtual machines from the hypervisor.<br>            Failed<br>                Job failed for reasons specified in TaskStateInformation.<br>            Canceled<br>                Indicates that the task was stopped by user intervention (using Stop-ProvTask)<br>        TaskStateInformation<br>            Provides more detailed information about the current task state.<br>        VirtualMachinesToRemoveCount <int><br>            The total number of virtual machines that the task is trying to remove.<br>        VirtualMachinesRemovedCount <int><br>            The number of virtual machines that the task has removed so far.  Details of the machines that have been removed are in the RemovedVirtualMachines parameter.<br>        VirtualMachinesFailedCount <int><br>            The number of virtual machines that the task has failed to remove.  Details of the machines that failed are in the FailedVirtualMachines parameter.<br>        FailedVirtualMachines <Citrix.DesktopUpdateManager.SDK.VirtualMachineCreation[]><br>            ADAccountName <string><br>                The domain-qualified AD Account name of the machine.<br>            ADAccountSid <string><br>                The AD account SID of the machine account.<br>            DiagnosticInformation <Citrix.MachineCreation.Sdk.ExceptionSurrogate[]><br>                A collection of handled error states which caused the provisioning to fail.<br>                    ExceptionType <string><br>                      The type of exception this object represents<br>                    Message  <string><br>                      The exception message<br>                    Details  <string><br>                      The full exception content including stack trace<br>                    InnerException <Citrix.MachineCreation.Sdk.ExceptionSurrogate><br>                      Information relating to any contributing error state<br>            Status <string><br>            StatusAdditionalInformation <string><br>            VMId <string><br>                The virtual machine identifier in the hypervisor.<br>            VMName <string><br>                The display name of the virtual machine in the hypervisor.<br>        RemovedVirtualMachines <Citrix.DesktopUpdateManager.SDK.VirtualMachineCreation[]><br>            See FailedVirtualMachines for details of the object parameters.<br>        ProgressEstimator<br>            Gives an estimate of the number of virtual machines processed, averaging over virtual machines that were both partly and completely processed.
   ## Notes
   Only one long-running task for each provisioning scheme can be processed at a time.<br>    This task still operates if the hosting unit or VMs in the hypervisor are missing. This removes the data from the Citrix Machine Creation Services, but the VMs remain in the hypervisor.<br>    In the case of failure, the following errors can result.<br>    Error Codes<br>    -----------<br>    JobCreationFailed<br>    The requested task could not be started.<br>    DatabaseError<br>    An error occurred in the service while attempting a database operation.<br>    DatabaseNotConfigured<br>    The operation could not be completed because the database for the service is not configured.<br>    ServiceStatusInvalidDb<br>    An error occurred in the service while attempting a database operation. Communication with the database failed for<br>    for various reasons.<br>    WorkflowHostUnavailable<br>    The task could not be started because the database connection is inactive.<br>    CommunicationError<br>    An error occurred while communicating with the service.<br>    InvalidParameterCombination<br>    Both PurgeJobOnSuccess and RunAsynchronously were specified. When running asynchronously, the cmdlet terminates before the job does, so it cannot clean up the completed job.<br>    PermissionDenied<br>    The user does not have administrative rights to perform this operation.<br>    ConfigurationLoggingError<br>    The operation could not be performed because of a configuration logging error<br>    ExceptionThrown<br>    An unexpected error occurred. To locate more details, see the Windows event logs on the controller being used or examine the XenDesktop logs.<br>    The cmdlet is associated with a task of type RemoveVirtualMachine, and while active will move through the following operations (CurrentOperation field)<br>    ValidatingInputs<br>    RemovingVirtualMachines
## Examples

### EXAMPLE 1
```
c:\PS>,(Get-ProvVM -ProvisioningSchemeName XenPS) | Remove-ProvVM XenPS

TaskId                       : cfb506a5-cc7e-4a49-ac7b-dd960029d0d3
Active                       : False
Host                         : DDC
DateStarted                  : 10/10/2012 16:39:45
Metadata                     : {}
WorkflowStatus               : Completed
ProvisioningSchemeUid        : e1afc8fb-3f52-42ea-9a17-305fdb0b6ee4
ProvisioningSchemeName       : XenPS
TaskState                    : Finished
TaskStateInformation         :
VirtualMachinesToRemoveCount : 2
RemovedVirtualMachines       : {XD\IP0001$, XD\IP0002$}
FailedVirtualMachines        : {}
VirtualMachinesRemovedCount  : 2
VirtualMachinesFailedCount   : 0
ProgressEstimator            : 2
Type                         : RemoveVirtualMachine
Status                       : Finished
CurrentOperation             :
TaskProgress                 : 100
TaskExpectedCompletion       : 10/10/2012 16:39:50
LastUpdateTime               : 10/10/2012 16:39:50
ActiveElapsedTime            : 5
DateFinished                 : 10/10/2012 16:39:50
TerminatingError             :
```
   Description<br>-----------<br>Remove all VMs from provisioning scheme XenPS
