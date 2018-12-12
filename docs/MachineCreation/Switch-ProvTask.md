
# Switch-Provtask
Moves all MachineCreation Service tasks from the current execution host to another.
## Syntax
```
Switch-ProvTask [-Host2] <String> [-LoggingId <Guid>] [-BearerToken <String>] [-AdminAddress <String>] [<CommonParameters>]
```
## Detailed Description
Enables tasks running within the MachineCreation Service to be moved from one execution host to a different host.

Tasks can only execute on a single host.  If the host is removed from a deployment, the tasks cannot continue to execute.  These 'orphaned' tasks can be moved to a different host within the deployment so that they can continue to execute.  All tasks must be moved; there is no mechanism to move individual tasks.  Run the Switch-ProvTask command against the host to which the tasks are to be moved; that is, if you are not running the command directly on the host, use the AdminAddress parameter to specify the host to which tasks will be moved.


## Related Commands

* [Get-ProvTask](./Get-ProvTask/)
* [Stop-ProvTask](./Stop-ProvTask/)
* [Remove-ProvTask](./Remove-ProvTask/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| Host2 | Specifies the host from which the tasks should be removed. | true | false |  |
| LoggingId | Specifies the identifier of the high-level operation this cmdlet call forms a part of. Citrix Studio and Director typically create high-level operations. PowerShell scripts can also wrap a series of cmdlet calls in a high-level operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller the PowerShell snap-in will connect to. You can provide this as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type

### 

## Return Values

### 

## Notes
If the command fails, the following errors can result.<br>    Error Codes<br>    -----------<br>    PartialData<br>        Only a subset of the requested data was returned.<br>    NoOp<br>        The operation was successful but had no effect.<br>    DatabaseError<br>        An error occurred in the service while attempting a database operation.<br>    DatabaseNotConfigured<br>        The operation could not be completed because the database for the service is not configured.<br>    DataStoreException<br>        An error occurred in the service while attempting a database operation - communication with the database failed for various reasons.<br>    PermissionDenied<br>        You do not have permission to execute this command.<br>    AuthorizationError<br>        There was a problem communicating with the Citrix Delegated Administration Service.<br>    ConfigurationLoggingError<br>        The operation could not be performed because of a configuration logging error.<br>    CommunicationError<br>        There was a problem communicating with the remote service.<br>    ExceptionThrown<br>        An unexpected error occurred.  For more details, see the Windows event logs on the controller or the XenDesktop logs.
## Examples

### Example 1
```
c:\PS>Switch-ProvTask -Host CRASHED

Success
```
#### Description
Transfer the execution of tasks that had been executing on the MachineCreation Service instance on host CRASHED to the local instance.
