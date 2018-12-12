
# Unlock-Provscheme
Unlocks a Provisioning Scheme.
## Syntax
```
Unlock-ProvScheme [-ProvisioningSchemeName] <String> [-LoggingId <Guid>] [-BearerToken <String>] [-AdminAddress <String>] [<CommonParameters>]

Unlock-ProvScheme -ProvisioningSchemeUid <Guid> [-LoggingId <Guid>] [-BearerToken <String>] [-AdminAddress <String>] [<CommonParameters>]
```
## Detailed Description
Provides the ability to unlock a provisioning scheme that has the Id of a failed Task still associated with it. This allows another long-running task to operate on that scheme. The cmdlet will not unlock a scheme with a task still marked as being active.  Use Stop-ProvTask (or, if the task is registered with a failed server, Switch-ProvTask and Stop-ProvTask) to stop any active task first.


## Related Commands

* [Get-ProvScheme](./Get-ProvScheme/)
* [Stop-ProvTask](./Stop-ProvTask/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| ProvisioningSchemeName | The name of the provisioning scheme. | true | true (ByPropertyName) |  |
| ProvisioningSchemeUid | The unique identifier of the provisioning scheme. | true | false |  |
| LoggingId | Specifies the identifier of the high-level operation this cmdlet call forms a part of. Citrix Studio and Director typically create high-level operations. PowerShell scripts can also wrap a series of cmdlet calls in a high-level operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snap-in connects to.  You can provide this as a host name or an IP address. | false | false | LocalHost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type

### 

## Return Values

### 

## Notes
In the case of failure, the following errors can result.<br>    Error Codes<br>    -----------<br>    ProvisioningSchemeNotFound<br>    The specified provisioning scheme could not be located.<br>    NoOp<br>    The specified provisioning scheme had no task object associated.<br>    TaskActive<br>    The task object associated with the provisioning scheme is still active.<br>    DatabaseError<br>    An error occurred in the service while attempting a database operation.<br>    CouldNotQuueryDatabase<br>    The query required to get the database was not defined.<br>    CommunicationError<br>    An error occurred while communicating with the service.<br>    InvalidFilter<br>    A filtering expression was supplied that could not be interpreted for this cmdlet.<br>    PermissionDenied<br>    The user does not have administrative rights to perform this operation.<br>    ConfigurationLoggingError<br>    The operation could not be performed because of a configuration logging error<br>    ExceptionThrown<br>    An unexpected error occurred.  To locate more details, see the Windows event logs on the controller being used or examine the XenDesktop logs.
## Examples

### Example 1
```
C:\PS>Unlock-ProvScheme -provisioningSchemeName MyScheme
```
#### Description
Unlocks the provisioning scheme 'MyScheme'.
