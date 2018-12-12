
# New-Provvm
Creates a new virtual machine.
## Syntax
```
New-ProvVM -ProvisioningSchemeName <String> -ADAccountName <String[]> [-FastBuild] [-NetworkMapping <Hashtable>] [-AutoAssignVLAN] [-SecurityGroup <String[]>] [-MachinesPerAssistant <Int32>] [-MaxAssistants <Int32>] [-RunAsynchronously] [-PurgeJobOnSuccess] [-LoggingId <Guid>] [-BearerToken <String>] [-AdminAddress <String>] [<CommonParameters>]

New-ProvVM -ProvisioningSchemeUid <Guid> -ADAccountName <String[]> [-FastBuild] [-NetworkMapping <Hashtable>] [-AutoAssignVLAN] [-SecurityGroup <String[]>] [-MachinesPerAssistant <Int32>] [-MaxAssistants <Int32>] [-RunAsynchronously] [-PurgeJobOnSuccess] [-LoggingId <Guid>] [-BearerToken <String>] [-AdminAddress <String>] [<CommonParameters>]
```
## Detailed Description
Lets you create new virtual machines with the configuration specified by a provisioning scheme.

The virtual machines are created using all of the storage specified in the provisioning scheme. The storage is used in a round robin mechanism. For the duration of this task, the AD accounts are locked (by the AD Identity Service), which stops the same accounts being used by other virtual machine creation tasks.


## Related Commands

* [Get-ProvVM](./Get-ProvVM/)
* [Remove-ProvVM](./Remove-ProvVM/)
* [Lock-ProvVM](./Lock-ProvVM/)
* [Unlock-ProvVM](./Unlock-ProvVM/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| ProvisioningSchemeName | The name of the provisioning scheme in which the virtual machines are created. | true | false |  |
| ProvisioningSchemeUid | The unique identifier for the provisioning scheme in which the virtual machines are created. | true | false |  |
| ADAccountName | A list of the Active Directory account names that are used for the virtual machines. The accounts must be provided in a domain-qualified format. This parameter accepts Identity objects as returned by the New-AcctADAccount cmdlet, or any PSObject with string properties "Domain" and "ADAccountName". | true | false |  |
| FastBuild | Indicates whether or not the command can improve speed by using optimizations in the creation process. This may mean that machines you create cannot be booted until ResetVM operations have been performed by the Broker and Machine Identity Services. | false | false |  |
| NetworkMapping | Specifies how the attached NICs are mapped to networks. If this parameter is omitted, provisioned VMs are created with network settings as inherited from the provisioning scheme. If this parameter is supplied, machines are created with the number of NICs specified in the map, and each NIC is attached to the specified network. | false | false |  |
| AutoAssignVLAN | Indicates whether or not the VLAN of the network should be automatically assigned to the new VM or if the VLAN from the master image should be used | false | false | false |
| SecurityGroup | The security groups to apply to machines created in Cloud Hypervisors | false | false |  |
| MachinesPerAssistant | The number of concurrent volume operations that may be performed by each volume worker helper machine | false | false |  |
| MaxAssistants | The maximum number of volume worker help machines that may be created for this operation. | false | false |  |
| RunAsynchronously | Indicates whether or not the command returns before it is complete. If specified, the command returns an identifier for the task that was created. This task can be monitored using the get-ProvTask command. | false | false | false |
| PurgeJobOnSuccess | Indicates that the task history is removed from the database when the task has finished. This cannot be specified for tasks that are run asynchronously. | false | false |  |
| LoggingId | Specifies the identifier of the high-level operation this cmdlet call forms a part of. Citrix Studio and Director typically create high-level operations. PowerShell scripts can also wrap a series of cmdlet calls in a high-level operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller to which the PowerShell snap-in connects. You can provide this as a host name or an IP address. | false | false | LocalHost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type

### 

## Return Values

### System.Guid
When the RunAsynchronously identifier is specified, this GUID is returned and provides the task identifier.<br>System.Management.Automation.PSCustomObject<br>    This object provides details of the task that was run and contains the following information:<br>        TaskId &lt;Guid&gt;<br>            The identifier for the task that was performed.<br>        Active &lt;Boolean&gt;<br>            Indicates whether the task is still processing or is complete.<br>        Host &lt;string&gt;<br>            The name of the host on which the task is running or was run.<br>        DateStarted &lt;DateTime&gt;<br>            The date and time that the task was initiated.<br>        Type &lt;Citrix.XDInterServiceTypes.JobType&gt;<br>            The type of task. For newly provisioned VM tasks, this is always "NewVirtualMachine".<br>        Metadata &lt;Citrix.MachineCreation.Sdk.Metadata\[\]&gt;<br>            The list of metadata stored against the task. For new tasks this is empty until metadata is added.<br>        WorkflowStatus &lt;System.Workflow.Runtime.WorkflowStatus&gt;<br>            Indicates the status of the workflow that is used to process the task.<br>        ProvisioningSchemeName &lt;string&gt;<br>            The name of the provisioning scheme that the task was for.<br>        ProvisioningSchemeUid &lt;Guid&gt;<br>            The unique identifier of the provisioning scheme that the task was for.<br>        MasterImage &lt;string&gt;<br>            The path (in the hosting unit provider) of the virtual machine snapshot that was used as the master image for the task.<br>        IdentityPoolName &lt;string&gt;<br>            The name of the identity pool (from the ADIdentity PowerShell snap-in) that the new provisioning scheme uses.<br>        IdentityPoolUid &lt;guid&gt;<br>            The unique identifier name of the identity pool (from the ADIdentity PowerShell snap-in) that the new provisioning scheme uses.<br>        HostingUnitName &lt;string&gt;<br>            The name of the hosting unit (from the Hosting Unit PowerShell snap-in) that the new provisioning scheme uses.<br>        HostingUnitUid<br>            The unique identifier of the hosting unit (from the Hosting Unit PowerShell snap-in) that the new provisioning scheme uses.<br>        TaskState &lt;Citrix.DesktopUpdateManager.SDK.ProvisionVMState&gt;<br>            The state of the task.  This can be any of the following:<br>            Processing<br>                Indicates that the task is in its initial state.<br>            LocatingResources,<br>                Indicates that the task is locating information from other services.<br>            HostingUnitNotFound<br>                Indicates that the required hosting unit could not be located.<br>            ProvisioningSchemeNotFound<br>                Indicates that the required provisioning scheme could not be located.<br>            Provisioning<br>                Indicates that the task is at the provisioning stage.<br>            IdentityPoolNotFound<br>                Indicates that the required identity pool could not be located.<br>            TaskAlreadyRunningForProvisioningScheme<br>                Indicates that the provisioning scheme already has another task running.<br>            HypervisorInMaintenanceMode<br>                Indicates that the hypervisor is not available for normal use.<br>            NoAvailableStorage<br>                Indicates that no storage is available for the hypervisor.<br>            NoAvailableNetwork<br>                Indicates that no network is available for the hypervisor.<br>            Finalizing<br>                Indicates that the task is finalizing.<br>            Finished<br>                Indicates that the task is complete.<br>            FinishedWithErrors<br>                Indicates that the task is complete but there were errors. Specific details of errors are included with each failed virtual machine.<br>            Removing<br>                Indicates that the task is removing virtual machines from the hypervisor.<br>            Failed<br>                The job failed for reasons specified in TaskStateInformation.<br>            Canceled<br>                Indicates that the task was stopped by user intervention (using Stop-ProvTask).<br>        TaskStateInformation<br>            Provides more detailed information about the current task state.<br>        VirtualMachinesToCreateCount &lt;int&gt;<br>            The total number of virtual machines that the task is trying to create.<br>        VirtualMachinesCreatedCount &lt;int&gt;<br>            The number of virtual machines that the task has created so far. Details of the machines that were created are in the CreatedVirtualMachines parameter.<br>        VirtualMachinesCreationFailedCount &lt;int&gt;<br>            The number of virtual machines that the task has failed to create. Details of the machines that were not created are in the FailedVirtualMachines parameter.<br>        FailedVirtualMachines &lt;Citrix.DesktopUpdateManager.SDK.VirtualMachineCreation\[\]&gt;<br>            ADAccountName &lt;string&gt;<br>                The domain qualified AD Account name of the machine.<br>            ADAccountSid &lt;string&gt;<br>                The AD account SID of the machine account.<br>            DiagnosticInformation &lt;Citrix.MachineCreation.Sdk.ExceptionSurrogate\[\]&gt;<br>                A collection of handled error states which caused the provisioning to fail.<br>                    ExceptionType &lt;string&gt;<br>                      The type of exception this object represents<br>                    Message  &lt;string&gt;<br>                      The exception message<br>                    Details  &lt;string&gt;<br>                      The full exception content including stack trace<br>                    InnerException &lt;Citrix.MachineCreation.Sdk.ExceptionSurrogate&gt;<br>                      Information relating to any contributing error state<br>            Status &lt;string&gt;<br>            StatusAdditionalInformation &lt;string&gt;<br>            VMId &lt;string&gt;<br>                The virtual machine identifier within the hypervisor in which the VM resides.<br>            VMName &lt;string&gt;<br>                The display name of the virtual machine within the hypervisor in which the VM resides.<br>        CreatedVirtualMachines &lt;Citrix.DesktopUpdateManager.SDK.VirtualMachineCreation\[\]&gt;<br>            See FailedVirtualMachines for details of the object parameters.
## Notes
Only one long-running task in each provisioning scheme can be processed at a time.<br>    In the case of failure, the following errors can result.<br>    Error Codes<br>    -----------<br>    JobCreationFailed<br>    The requested task could not be started.<br>    DatabaseError<br>    An error occurred in the service while attempting a database operation.<br>    DatabaseNotConfigured<br>    The operation could not be completed because the database for the service is not configured.<br>    ServiceStatusInvalidDb<br>    An error occurred in the service while attempting a database operation. Communication with the database failed<br>    for various reasons.<br>    WorkflowHostUnavailable<br>    The task could not be started because the database connection is inactive.<br>    PermissionDenied<br>    The user does not have administrative rights to perform this operation.<br>    ConfigurationLoggingError<br>    The operation could not be performed because of a configuration logging error<br>    CommunicationError<br>    An error occurred while communicating with the service.<br>    InvalidParameterCombination<br>    Both PurgeJobOnSuccess and RunAsynchronously were specified.<br>    When running asynchronously, the cmdlet terminates before the job does,<br>    so it cannot clean up the completed job.<br>    PermissionDenied<br>    The user does not have administrative rights to perform this operation.<br>    ExceptionThrown<br>    An unexpected error occurred. To locate more details, see the Windows event logs<br>    on the controller being used, or examine the XenDesktop logs.<br>    The cmdlet is associated with a task of type NewVirtualMachine, and while active will move through the following operations (CurrentOperation field)<br>    ValidatingInputs<br>    CreatingVirtualMachines<br>    ReleasingAccountLocks
## Examples

### Example 1
```
C:\PS>New-provVM -ProvisioningSchemeName MyScheme -ADAccountName "domain\Account"

TaskId                             : 4b49f13a-277c-4cb0-bc40-f088430cfe8a

Active                             : False

Host                               : DUMTESTDDC

DateStarted                        : 18/05/2010 10:54:32

Type                               : NewVirtualMachine

Metadata                           : {}

WorkflowStatus                     : Completed

MasterImage                        : /Base.vm/Base.snapshot

ProvisioningSchemeName             : MyScheme

ProvisioningSchemeUid              : 7585f0de-192e-4847-a6d8-22713c3a2f42

CurrentOperation                   :

TaskState                          : Finished

TaskStateInformation               :

HostingUnitUid                     : 01a4a008-8ce8-4165-ba9c-cdf15a6b0501

HostingUnitName                    : XenHU

IdentityPoolUid                    : 03743136-e43b-4a87-af74-ab71686b3c16

IdentityPoolName                   : idPool1

VirtualMachinesToCreateCount       : 1

VirtualMachinesCreatedCount        : 1

VirtualMachinesCreationFailedCount : 0

CreatedVirtualMachines             : {DOMAIN\Account$}

FailedVirtualMachines              : {}

ProvisioningJob                    : 6fa5dc7c-6d49-4616-8682-aeb1580866b3

ProvisioningStatus                 : Completed
```
#### Description
Creates a new virtual machine using the AD account "domain\\account" in the provisioning scheme "MyScheme".
### Example 2
```
C:\PS>New-provVM -ProvisioningSchemeName MyScheme -ADAccountName "domain\Account" -RunAsynchronously

Guid

----

6dd85fec-96cf-46b1-9cd4-d8ba7d06e85b
```
#### Description
Creates a new virtual machine using the AD account "domain\\account" in the provisioning scheme "MyScheme" asynchronously. To get the task details, use Get-ProvTask -TaskID &lt;task id&gt;&lt;br&gt;i.e.&lt;br&gt;C:\\PS&gt;Get-ProvTask -TaskID 6dd85fec-96cf-46b1-9cd4-d8ba7d06e85b&lt;br&gt;TaskId                             : 4b49f13a-277c-4cb0-bc40-f088430cfe8a&lt;br&gt;Active                             : False&lt;br&gt;Host                               : MyHost&lt;br&gt;DateStarted                        : 18/05/2010 10:54:32&lt;br&gt;Type                               : NewVirtualMachine&lt;br&gt;Metadata                           : {}&lt;br&gt;WorkflowStatus                     : Completed&lt;br&gt;MasterImage                        : /Base.vm/Base.snapshot&lt;br&gt;ProvisioningSchemeName             : MyScheme&lt;br&gt;ProvisioningSchemeUid              : 7585f0de-192e-4847-a6d8-22713c3a2f42&lt;br&gt;TaskState                          : Finished&lt;br&gt;TaskStateInformation               :&lt;br&gt;HostingUnitUid                     : 01a4a008-8ce8-4165-ba9c-cdf15a6b0501&lt;br&gt;HostingUnitName                    : XenHU&lt;br&gt;IdentityPoolUid                    : 03743136-e43b-4a87-af74-ab71686b3c16&lt;br&gt;IdentityPoolName                   : idPool1&lt;br&gt;VirtualMachinesToCreateCount       : 1&lt;br&gt;VirtualMachinesCreatedCount        : 1&lt;br&gt;VirtualMachinesCreationFailedCount : 0&lt;br&gt;CreatedVirtualMachines             : {DOMAIN\\Account\$}&lt;br&gt;FailedVirtualMachines              : {}&lt;br&gt;ProvisioningJob                    : 6fa5dc7c-6d49-4616-8682-aeb1580866b3&lt;br&gt;ProvisioningStatus                 : Completed
### Example 3
```
C:\PS>$accounts = Get-AcctAdAccount -IdentityPool MyPool -State Available

C:\PS>New-provVM -ProvisioningSchemeName MyScheme -ADAccountName $t -RunAsyncronously
```
#### Description
Creates a new virtual machine using all of the available AD accounts from the identity pool "MyPool" in the provisioning scheme "MyScheme" asynchronously. To get the task details, use Get-ProvTask -TaskID &lt;task id&gt;&lt;br&gt;For example:&lt;br&gt;C:\\PS&gt;Get-ProvTask -TaskID 6dd85fec-96cf-46b1-9cd4-d8ba7d06e85b&lt;br&gt;TaskId                             : 4b49f13a-277c-4cb0-bc40-f088430cfe8a&lt;br&gt;Active                             : False&lt;br&gt;Host                               : MyHost&lt;br&gt;DateStarted                        : 18/05/2010 10:54:32&lt;br&gt;Type                               : NewVirtualMachine&lt;br&gt;Metadata                           : {}&lt;br&gt;WorkflowStatus                     : Completed&lt;br&gt;MasterImage                        : /Base.vm/Base.snapshot&lt;br&gt;ProvisioningSchemeName             : MyScheme&lt;br&gt;ProvisioningSchemeUid              : 7585f0de-192e-4847-a6d8-22713c3a2f42&lt;br&gt;TaskState                          : Finished&lt;br&gt;TaskStateInformation               :&lt;br&gt;HostingUnitUid                     : 01a4a008-8ce8-4165-ba9c-cdf15a6b0501&lt;br&gt;HostingUnitName                    : XenHU&lt;br&gt;IdentityPoolUid                    : 03743136-e43b-4a87-af74-ab71686b3c16&lt;br&gt;IdentityPoolName                   : idPool1&lt;br&gt;VirtualMachinesToCreateCount       : 1&lt;br&gt;VirtualMachinesCreatedCount        : 1&lt;br&gt;VirtualMachinesCreationFailedCount : 0&lt;br&gt;CreatedVirtualMachines             : {DOMAIN\\Account\$}&lt;br&gt;FailedVirtualMachines              : {}&lt;br&gt;ProvisioningJob                    : 6fa5dc7c-6d49-4616-8682-aeb1580866b3&lt;br&gt;ProvisioningStatus                 : Completed
