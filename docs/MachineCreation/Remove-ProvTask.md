﻿
# Remove-Provtask
Removes from the database completed tasks for the MachineCreation Service.
## Syntax
```
Remove-ProvTask [-TaskId] <Guid> [-LoggingId <Guid>] [-BearerToken <String>] [-AdminAddress <String>] [<CommonParameters>]
```
## Detailed Description
Enables completed tasks that have run within the MachineCreation Service to be removed from the database.


## Related Commands

* [Get-ProvTask](./Get-ProvTask/)
* [Add-ProvTaskMetadata](./Add-ProvTaskMetadata/)
* [Remove-ProvTaskMetadata](./Remove-ProvTaskMetadata/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| TaskId | Specifies the identifier for the task to be removed. | true | true (ByPropertyName) |  |
| LoggingId | Specifies the identifier of the high-level operation this cmdlet call forms a part of. Citrix Studio and Director typically create high-level operations. PowerShell scripts can also wrap a series of cmdlet calls in a high-level operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller the PowerShell snap-in will connect to. You can provide this as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type

### System.Management.Automation.Psobject
Objects containing the TaskId parameter can be piped to the Remove-ProvTask command.
## Return Values

### 

## Notes
If the command fails, the following errors can result.<br>    Error Codes<br>    -----------<br>    InvalidParameterCombination<br>        The cmdlet parameters are inconsistent.<br>    InvalidWorkflow<br>        The specified task could not be found.<br>    InvalidWorkflowState<br>        The task was not in an appropriate state for the requested operation.<br>    DatabaseError<br>        An error occurred in the service while attempting a database operation.<br>    DatabaseNotConfigured<br>        The operation could not be completed because the database for the service is not configured.<br>    DataStoreException<br>        An error occurred in the service while attempting a database operation - communication with the database failed for various reasons.<br>    PermissionDenied<br>        You do not have permission to execute this command.<br>    AuthorizationError<br>        There was a problem communicating with the Citrix Delegated Administration Service.<br>    ConfigurationLoggingError<br>        The operation could not be performed because of a configuration logging error.<br>    CommunicationError<br>        There was a problem communicating with the remote service.<br>    ExceptionThrown<br>        An unexpected error occurred.  For more details, see the Windows event logs on the controller or the XenDesktop logs.
## Examples

### Example 1
```
c:\PS>Get-ProvTask -active $false | Remove-ProvTask

Success
```
#### Description
Remove entries for all completed tasks from the MachineCreation Service.
