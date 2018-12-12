
# Publish-Provmastervmimage
Update the master image associated with the provisioning scheme.
## Syntax
```
Publish-ProvMasterVMImage [-ProvisioningSchemeName] <String> -MasterImageVM <String> [-VhdTemplateSource <String>] [-VhdResultDestination <String>] [-AppScanResultsFile <String>] [-FunctionalLevel <String>] [-RunAsynchronously] [-PurgeJobOnSuccess] [-DoNotStoreOldImage] [-LoggingId <Guid>] [-BearerToken <String>] [-AdminAddress <String>] [<CommonParameters>]

Publish-ProvMasterVMImage -ProvisioningSchemeName <String> [-DoNotStoreOldImage] [-LoggingId <Guid>] [-BearerToken <String>] [-AdminAddress <String>] [<CommonParameters>]

Publish-ProvMasterVMImage -ProvisioningSchemeUid <Guid> -MasterImageVM <String> [-VhdTemplateSource <String>] [-VhdResultDestination <String>] [-AppScanResultsFile <String>] [-FunctionalLevel <String>] [-RunAsynchronously] [-PurgeJobOnSuccess] [-DoNotStoreOldImage] [-LoggingId <Guid>] [-BearerToken <String>] [-AdminAddress <String>] [<CommonParameters>]

Publish-ProvMasterVMImage -ProvisioningSchemeUid <Guid> [-DoNotStoreOldImage] [-LoggingId <Guid>] [-BearerToken <String>] [-AdminAddress <String>] [<CommonParameters>]
```
## Detailed Description
Provides the ability to update the hard disk image used to provision virtual machines. If the provisioning scheme is a 'CleanOnBoot' type, then the next time that virtual machines are started, their hard disks are updated to this new image.  Regardless of the 'CleanOnBoot' type, all new virtual machines created after this command will use this new hard disk image.

A background task will be created to remove the old hard disk copies.  You can locate and monitor this task using the Get-ProvTask cmdlet.

A snapshot or VM template is used rather than a VM, so that the content of the hard disk for the provisioning scheme can be easily determined.

As the snapshot or VM template are specified using a path into the Citrix Host Service PowerShell Provider, the Citrix Host Service PowerShell snap-in must also be loaded for this cmdlet to be used.

The previous hard disk image path is stored into the history (see Get-ProvSchemeMasterVMImageHistory).  The data stored in the history allows for a rollback to be undertaken, to revert to the previous hard disk image if required.


## Related Commands

* [Get-ProvSchemeMasterVMImageHistory](./Get-ProvSchemeMasterVMImageHistory/)
* [Get-ProvScheme](./Get-ProvScheme/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| ProvisioningSchemeName | The provisioning scheme to which the hard disk image should be updated. | true | true (ByPropertyName) |  |
| MasterImageVM | The path in the hosting unit provider to the virtual machine snapshot or VM template that will be used.  This identifies the hard disk to be used and the default values for the memory and processors.  This must be a path to a Snapshot or Template item in the hosting unit that the hosting unit name or hosting unit Uid refers to.<br>Valid paths are of the format; XDHyp:\\HostingUnits\\&lt;HostingUnitName&gt;\\&lt;path&gt;\\&lt;VMName&gt;.vm\\&lt;SnapshotName&gt;.snapshot XDHyp:\\HostingUnits\\&lt;HostingUnitName&gt;\\&lt;path&gt;\\&lt;TemplateName&gt;.template | true | true (ByPropertyName) |  |
| ProvisioningSchemeUid | The provisioning scheme identifier to which the hard disk image should be updated. | true | false |  |
| VhdTemplateSource | A file path to a source VHD template to be used when performing application scanning during image preparation. The presence of this parameter in conjunction with VhdResultDestination implies that application scanning is to be performed | false | false |  |
| VhdResultDestination | A file path (including file name) where the VHD disk file containing the results of application scanning should be written. | false | false |  |
| AppScanResultsFile | File name to which the results of application scanning should be written. | false | false |  |
| FunctionalLevel | The FunctionalLevel of the VDA installed on the given MasterImageVM. | false | false |  |
| RunAsynchronously | Indicates whether or not the cmdlet should return before it is complete.  If specified, the command returns an identifier for the task that was created.  You can monitor this task using the get-ProvTask cmdlet. | false | false | false |
| PurgeJobOnSuccess | Indicates that the task history will be removed from the database once the task has finished.  This cannot be specified for tasks that are run asynchronously. | false | false | false |
| DoNotStoreOldImage | Specifies that the current image should not be added to the image history list for the provisioning scheme. This is useful when rolling back to a previous image. | false | false |  |
| LoggingId | Specifies the identifier of the high-level operation this cmdlet call forms a part of. Citrix Studio and Director typically create high-level operations. PowerShell scripts can also wrap a series of cmdlet calls in a high-level operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller the PowerShell snap-in will connect to. You can provide this as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type

### 

## Return Values

### System.Guid
When "RunAsynchronously" is specified, this identifier is returned to provide the task identifier.<br>System.Management.Automation.PSCustomObject<br>    This object provides details of the task run and contains the following information:<br>        TaskId &lt;Guid&gt;<br>            The identifier for the task that was performed.<br>        Active &lt;Boolean&gt;<br>            Indicates whether the task is still processing or is complete.<br>        Host &lt;string&gt;<br>            The name of the host on which the task is running or was run.<br>        DateStarted &lt;DateTime&gt;<br>            The date and time that the task was initiated.<br>        Type &lt;Citrix.XDInterServiceTypes.JobType&gt;<br>            The type of the task.  For new provisioning scheme tasks this is always "NewProvisioningScheme".<br>        Metadata &lt;Citrix.MachineCreation.Sdk.Metadata\[\]&gt;<br>            The list of metadata stored against the task.  For new tasks this will be empty until metadata is added.<br>        WorkflowStatus &lt;System.Workflow.Runtime.WorkflowStatus&gt;<br>            Indicates the status of the workflow that is being used to process the task.<br>        ProvisioningSchemeName &lt;string&gt;<br>            The name of the provisioning scheme that the task was for.<br>        ProvisioningSchemeUid &lt;Guid&gt;<br>            The unique identifier of the provisioning scheme that the task was for.<br>        MasterImage &lt;string&gt;<br>            The path (in the hosting unit provider) of the virtual machine snapshot or VM template that was used as the master image for the task.<br>        IdentityPoolName &lt;string&gt;<br>            The name of the identity pool (from the ADIdentity PowerShell snap-in) that the new provisioning scheme will use.<br>        IdentityPoolUid &lt;guid&gt;<br>            The unique identifier name of the identity pool (from the ADIdentity PowerShell snap-in) that the new provisioning scheme will use.<br>        HostingUnitName &lt;string&gt;<br>            The name of the hosting unit (from the Hosting Unit PowerShell snap-in) that the new provisioning scheme will use.<br>        HostingUnitUid<br>            The unique identifier of the hosting unit (from the Hosting Unit PowerShell snap-in) that the new provisioning scheme will use.<br>        TaskState &lt;Citrix.DesktopUpdateManager.SDK.NewProvisioningSchemeState&gt;<br>            The state of the task.  This can be any of the following:<br>                Processing<br>                    Indicates that the task has just begun and has not done anything yet.<br>                LocatingResources,<br>                    Indicates that the workflow is locating resources from other services.<br>                HostingUnitNotFound<br>                    Indicates that the task failed because the required hosting unit could not be located.<br>                VirtualMachineSnapshotNotFound<br>                    Indicates that the task failed because the required snapshot or VM template could not be located.<br>                ConsolidatingMasterImage<br>                    Indicates that the task is consolidating the master image.<br>                ReplicatingConsolidatedImageToAllStorage<br>                    Indicates that the task is replicating the consolidated master image.<br>                StoringProvisioningScheme<br>                    Indicates that the task is storing the provisioning scheme data to the database.<br>                Finished<br>                    Indicates that the task has completed with no errors.<br>                ProvisioningSchemeAlreadyExists<br>                    Indicates that the task failed because a provisioning scheme with the same name already exists.<br>                IdentityPoolNotFound<br>                    Indicates that the task failed because the identity pool specified could not be found.<br>                MasterVMImageIsNotPartOfProvisioningSchemeHostingUnit,<br>                    Indicates that the hosting unit that the master image originated from is not the same hosting unit that the provisioning scheme is defined to use.<br>                MasterVmImageIsNotASnapshot<br>                    Indicates that the task failed because the master VM image path does not refer to a snapshot or a VM template item.<br>                ProvisioningSchemeNotFound<br>                    Could not find a provisioning scheme with the specified name.<br>                TaskAlreadyRunningForProvisioningScheme<br>                    A task for a provisioning scheme with the same name is already running.<br>                InvalidMasterVMConfiguration<br>                    The VM snapshot or VM template specified as the master had an invalid configuration.<br>                InvalidMasterVMState<br>                    The VM snapshot or VM template specified as the master is currently in an invalid state.<br>                InsufficientResources<br>                    Indicates that the task failed because the hypervisor did not have enough resources to complete the task.<br>                StorageNotFound<br>                    Indicates that no associated storage was found in the hosting unit.<br>                Canceled<br>                    Indicates that the task was stopped by user intervention (using Stop-ProvTask).<br>        TaskStateInformation &lt;string&gt;<br>            Holds string data providing more details about the current task state.<br>        TaskProgress<br>            The progress of the task 0-100%.
## Notes
Only one long-running task per provisioning scheme can be processed at any one time.<br>    In the case of failure, the following errors can result.<br>    Error Codes<br>    -----------<br>    JobCreationFailed<br>    The requested task could not be started.<br>    DatabaseError<br>    An error occurred in the service while attempting a database operation.<br>    DatabaseNotConfigured<br>    The operation could not be completed because the database for the service is not configured.<br>    ServiceStatusInvalidDb<br>    An error occurred in the service while attempting a database operation - communication with the database failed for<br>    for various reasons.<br>    WorkflowHostUnavailable<br>    The task could not be started because the database connection is inactive.<br>    CommunicationError<br>    An error occurred while communicating with the service.<br>    PermissionDenied<br>    The user does not have administrative rights to perform this operation.<br>    ConfigurationLoggingError<br>    The operation could not be performed because of a configuration logging error.<br>    ExceptionThrown<br>    An unexpected error occurred.  To locate more details, see the Windows event logs on the controller being used or examine the XenDesktop logs.<br>    The cmdlet is associated with a task of type PublishImage, and while active will move through the following operations (CurrentOperation field)<br>    ValidatingInputs<br>    ConsolidatingMasterImage<br>    PreparingMasterImage<br>    ReplicatingMasterImage<br>    CommittingScheme
## Examples

### Example 1
```
c:\PS>Publish-ProvMasterVMImage -ProvisioningSchemeName MyScheme -MasterImageVM XDHyp:\H

stingUnits\HostUnit1\RhoneCC_baseXP.vm\base.snapshot

TaskId                 : 248f102f-073f-45fe-aea9-1819a6d6dd1f

Active                 : False

Host                   : MyHost

DateStarted            : 17/05/2010 17:37:57

Type                   : PublishImage

Metadata               : {}

WorkflowStatus         : Completed

ProvisioningSchemeUid  : 7585f0de-192e-4847-a6d8-22713c3a2f42

ProvisioningSchemeName : MyScheme

MasterImage            : /RhoneCC_baseXP.vm/base.snapshot

HostingUnitName        : HostUnit1

HostingUnitUid         : 01a4a008-8ce8-4165-ba9c-cdf15a6b0501

ADIdentityPoolName     :

ADIdentityPoolUid      : 03743136-e43b-4a87-af74-ab71686b3c16

CurrentOperation       :

TaskState              : Finished

TaskStateInformation   :
```
#### Description
Updates the master hard disk image for the provisioning Scheme "MyScheme" to use the "base.snapshot" hard disk image.
