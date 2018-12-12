﻿
# Remove-Applibappdisk
Removes a AppDisk
## Syntax
```
Remove-AppLibAppDisk [-AppDiskName] <String> [-Force] [-RunAsynchronously] [-PurgeJobOnSuccess] [-LoggingId <Guid>] [-BearerToken <String>] [-AdminAddress <String>] [<CommonParameters>]

Remove-AppLibAppDisk -AppDiskUid <Guid> [-Force] [-RunAsynchronously] [-PurgeJobOnSuccess] [-LoggingId <Guid>] [-BearerToken <String>] [-AdminAddress <String>] [<CommonParameters>]
```
## Detailed Description
Provides the ability to remove an existing AppDisk, either the AppDisk name or the Uid can be used to identify the AppDisk to delete


## Related Commands

* [Get-AppLibTask](./Get-AppLibTask/)
* [New-AppLibAppDisk](./New-AppLibAppDisk/)
* [Set-AppLibAppDisk](./Set-AppLibAppDisk/)
* [Get-AppLibAppDisk](./Get-AppLibAppDisk/)
* [Import-AppLibAppDisk](./Import-AppLibAppDisk/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| AppDiskName | The name of the AppDisk to delete. | true | false |  |
| AppDiskUid | The Uid of the AppDisk to delete | true | true (ByPropertyName) |  |
| Force | Set this parameter to force the AppDisk to be deleted, by also abandoning any operations currently processing it. | false | false |  |
| RunAsynchronously | Indicates whether or not the command returns before it is complete. If specified, the command returns an identifier for the task that was created. This task can be monitored using the Get-AppLibTask command. | false | false | false |
| PurgeJobOnSuccess | Indicates that the task history is removed from the database when the task has finished. This can only be specified for tasks that are not run asynchronously. | false | false |  |
| LoggingId | Specifies the identifier of the high-level operation this cmdlet call forms a part of. Citrix Studio and Director typically create high-level operations. PowerShell scripts can also wrap a series of cmdlet calls in a high-level operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller the PowerShell snap-in will connect to. You can provide this as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type

### 

## Return Values

### System.Guid
When the RunAsynchronously identifier is specified, this GUID is returned and provides the task identifier
### System.Management.Automation.Pscustomobject
System.Management.Automation.PSCustomObject This object provides details of the task that was run and contains the following information:<br>TaskId &lt;Guid&gt; The identifier for the task that was performed. Active &lt;Boolean&gt; Indicates whether the task is still processing or is complete. Host &lt;string&gt; The name of the host on which the task is running or was run. DateStarted &lt;DateTime&gt; The date and time that the task was initiated. LastUpdateTime &lt;DateTime&gt; The date and time of the last task status update DateFinished &lt;DateTime&gt; The date and time that the task finished execution Metadata &lt;Metadata\[\]&gt; Associated key-value data TaskState &lt;string&gt; Where in its lifecycle the task is CurrentOperation &lt;string&gt; Operation specific phase of the overall "Running" task state. TerminatingError &lt; Citrix.Fma.Sdk.ServiceCore.CommonCmdlets.TaskterminatingError&gt; Diagnostic information in the case of a complete task failure ActiveElapsedTime &lt;int&gt; How many seconds of active execution the task has taken Type &lt;string&gt; The type of task. For this cmdlet's tasks, this is always DeleteAppDisk. AppDiskName &lt;string&gt; The name of the AppDisk that the task was for. AppDiskUid &lt;string&gt; The identifier of the AppDisk that the task was for. TaskStateInformation &lt;string&gt; Additional information about the current task state. TaskProgress &lt;double&gt; The progress of the task 0-100%. DiskLocalUid &lt;Guid&gt; The identifier of the AppDisk lineage. DiskLocalVersion &lt;Guid&gt; The identifier of the AppDisk within its lineage. HostingUnitName &lt;string&gt; The name of the associated hosting unit HostingUnitUid &lt;Guid&gt; The indentifier of the associated hosting unit VirtualDiskId &lt;Guid&gt; The identifier of the AppDisk stack ReservedMachineSid  &lt;string&gt; The associated reserved machine if any; the value may be empty for this operation depending on the previous state of the AppDisk.
## Notes
In the case of failure, the following errors can result.<br>    Error Codes<br>    -----------<br>    AppDiskNotFound<br>    The specified AppDisk could not be located.<br>    AppDiskInUse<br>    The specified AppDisk is currently in use.<br>    DatabaseError<br>    An error occurred in the service while attempting a database operation.<br>    DatabaseNotConfigured<br>    The operation could not be completed because the database for the service is not configured.<br>    ServiceStatusInvalidDb<br>    An error occurred in the service while attempting a database operation - communication with the database failed<br>    for various reasons.<br>    CommunicationError<br>    An error occurred while communicating with the service.<br>    PermissionDenied<br>    The user does not have administrative rights to perform this operation.<br>    ConfigurationLoggingError<br>    The operation could not be performed because of a configuration logging error<br>    ExceptionThrown<br>    An unexpected error occurred.  To locate more details, see the Windows event logs on the controller being used or examine the XenDesktop logs.
## Examples

### Example 1
```
C:\PS>Remove-AppLibAppDisk -AppDiskName "AppDiskName"

          TaskId                              : 90e93b9d-a225-4701-ad50-fa1546af35ac

          AppDiskName                         : MyAppDisk

          AppDiskUid                          : d9ba6487-05f8-48ad-a178-1794605e2b8e

          Active                              : False

          DiskLocalUid                        : 7b4c01c4-72fa-4c80-913d-c6df785f4297

          DiskLocalVersion                    : 25118c6e-a737-4fb9-b4b3-121910a73160

          DateStarted                         : 17/11/2015 09:15:22

          LastUpdateTime                      : 17/11/2015 09:16:18

          DateFinished                        : 17/11/2015 09:16:18

          Type                                : DeleteAppDisk

          Metadata                            : {}

          TaskState                           : Finished

          TaskStateInformation                :

          TaskProgress                        : 100

          TerminatingError                    :

          HostingUnitName                     : XenHU

          HostingUnitUid                      : 01a4a008-8ce8-4165-ba9c-cdf15a6b0501

          Host                                : MyHost

          VirtualDiskId                       : 7ce3c9a5-2888-45ba-8629-398f9e4eba7d

          CurrentOperation                    :

          ActiveElapsedTime                   : 56

          ReservedMachineSid                  :
```
#### Description
Removes the AppDisk with the name "AppDiskName"
### Example 2
```
C:\PS>Remove-AppLibAppDisk -AppDiskUid $AppDiskUid  -RunAsynchronously

          Guid

          ----

          6dd85fec-96cf-46b1-9cd4-d8ba7d06e85b
```
#### Description
Removes the AppDisk with the Uid \$AppDiskUid asynchronously. To get the task details, use Get-AppLibTask -TaskID &lt;task id&gt;&lt;br&gt;i.e.&lt;br&gt;C:\\PS&gt;Get-AppLibTask -TaskID 6dd85fec-96cf-46b1-9cd4-d8ba7d06e85b&lt;br&gt;TaskId                              : 6dd85fec-96cf-46b1-9cd4-d8ba7d06e85b AppDiskName                         : MyUpdatedAppDisk AppDiskUid                          : 3b9c6b62-be1e-467b-9cb4-025ad9cba916 Active                              : False DiskLocalUid                        : 7b4c01c4-72fa-4c80-913d-c6df785f4297 DiskLocalVersion                    : a23f8bae-dedf-433f-8908-025144ff4f81 DateStarted                         : 23/11/2015 13:15:53 LastUpdateTime                      : 23/11/2015 13:16:26 DateFinished                        : 23/11/2015 13:16:26 Type                                : NewAppDisk Metadata                            : {} TaskState                           : Finished TaskStateInformation                : TaskProgress                        : 100 TerminatingError                    : HostingUnitName                     : XenHU HostingUnitUid                      : 01a4a008-8ce8-4165-ba9c-cdf15a6b0501 Host                                : MyHost VirtualDiskId                       : 4c245ff7-5cdd-4aac-a854-1e101e23d1f6 CurrentOperation                    : ActiveElapsedTime                   : 33 ReservedMachineSid                  : S-1-5-21-2316621082-1546847349-2782505528-1165
