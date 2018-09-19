# Start-AppLibAppDiskAnalysis

   Starts an AppDNA analysis for an AppDisk

## Syntax
```
Start-AppLibAppDiskAnalysis [-AppDiskName] <String> [-RunAsynchronously] [-PurgeJobOnSuccess] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]

Start-AppLibAppDiskAnalysis -AppDiskUid <Guid> [-RunAsynchronously] [-PurgeJobOnSuccess] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
```

## Detailed Description
   AppDNA will analyse the chosen AppDisk to check for any compatability issues.

## Related Commands
  * [Get-AppLibTask](Get-AppLibTask/)
  * [Get-AppLibAppDisk](Get-AppLibAppDisk/)
  * [New-AppLibAppDisk](New-AppLibAppDisk/)
  * [Test-AppLibAppDiskNameAvailable](Test-AppLibAppDiskNameAvailable/)
## Parameters

| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| AppDiskName | The name of the AppDisk to analyse | true | false |  |
| AppDiskUid | The unique identifier of the App Disk to analyse | true | true (ByPropertyName) |  |
| RunAsynchronously | Indicates whether or not the command returns before it is complete. If specified, the command returns an identifier for the task that was created. This task can be monitored using the Get-AppLibTask command. | false | false | false |
| PurgeJobOnSuccess | Indicates that the task history is removed from the database when the task has finished. This can only be specified for tasks that are not run asynchronously. | false | false |  |
| LoggingId | Specifies the identifier of the high-level operation this cmdlet call forms a part of. Citrix Studio and Director typically create high-level operations. PowerShell scripts can also wrap a series of cmdlet calls in a high-level operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller the PowerShell snap-in will connect to. You can provide this as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type
### 
   
## Return Values
### System.Guid
   When the RunAsynchronously identifier is specified, this GUID is returned and provides the task identifier### System.Management.Automation.PSCustomObject
   System.Management.Automation.PSCustomObject This object provides details of the task that was run and contains the following information:<br>TaskId <Guid> The identifier for the task that was performed. Active <Boolean> Indicates whether the task is still processing or is complete. Host <string> The name of the host on which the task is running or was run. DateStarted <DateTime> The date and time that the task was initiated. LastUpdateTime <DateTime> The date and time of the last task status update DateFinished <DateTime> The date and time that the task finished execution Metadata <Metadata[]> Associated key-value data TaskState <string> Where in its lifecycle the task is CurrentOperation <string> Operation specific phase of the overall "Running" task state. TerminatingError < Citrix.Fma.Sdk.ServiceCore.CommonCmdlets.TaskterminatingError> Diagnostic information in the case of a complete task failure ActiveElapsedTime <int> How many seconds of active execution the task has taken Type <string> The type of task. For this cmdlet's tasks, this is always ImportAppDisk. AppDiskName <string> The name of the AppDisk that the task was for. AppDiskUid <string> The identifier of the AppDisk that the task was for. Scopes <Citrix.Fma.Sdk.ServiceCoreScopeReference[]> The delegated administration scopes to which the AppDisk will belong. TaskStateInformation <string> Additional information about the current task state. TaskProgress <double> The progress of the task 0-100%. DiskLocalUid <Guid> The identifier of the AppDisk lineage. DiskLocalVersion <Guid> The identifier of the AppDisk within its lineage. RemoteTaskId <Guid> The identifier of the associated disk management task on the Machine Creation Service HostingUnitName <string> The name of the associated hosting unit HostingUnitUid <Guid> The indentifier of the associated hosting unit VirtualDiskId <Guid> The identifier of the AppDisk stack DiskId <string> The hypervisor's identifier for the disk being imported RunAppDnaAnalysis <bool> Whether AppDNA analysis has been run ReservedMachineSid  <string> Security identifier of the VM being used to perform the operation## Notes
   Only one long-running task for each AppDisk can be processed at a time.<br>    In case of failure, the following errors can result.<br>    Error Codes<br>    -----------<br>    JobCreationFailed<br>    The requested task could not be started.<br>    DatabaseError<br>    An error occurred in the service while attempting a database operation.<br>    DatabaseNotConfigured<br>    The operation could not be completed because the database for the service is not configured.<br>    ServiceStatusInvalidDb<br>    An error occurred in the service while attempting a database operation. Communication with the database failed for<br>    for various reasons.<br>    CommunicationError<br>    An error occurred while communicating with the service.<br>    InvalidParameterCombination<br>    Both PurgeJobOnSuccess and RunAsynchronously were specified. When running asynchronously, the cmdlet terminates before the job does, so it cannot clean up the completed job.<br>    PermissionDenied<br>    The user does not have administrative rights to perform this operation.<br>    ConfigurationLoggingError<br>    The operation could not be performed because of a configuration logging error.<br>    ScopeNotFound<br>    One or more of the scopes nominated for the imported AppDisk do not exist.<br>    ExceptionThrown<br>    An unexpected error occurred. To locate more details, see the Windows event logs on the controller being used, or examine the XenDesktop logs.
