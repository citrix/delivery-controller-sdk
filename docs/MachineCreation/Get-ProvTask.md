# Get-ProvTask

   Gets the task history for the MachineCreation Service.

## Syntax
```
Get-ProvTask [[-TaskId] <Guid>] [-Type <JobType>] [-Active <Boolean>] [-Metadata <String>] [-Property <String[]>] [-ReturnTotalRecordCount] [-MaxRecordCount <Int32>] [-Skip <Int32>] [-SortBy <String>] [-Filter <String>] [-AdminAddress <String>] [<CommonParameters>]
```

## Detailed Description
   Returns a list of tasks that have run or are currently running within the MachineCreation Service.

## Related Commands
  * [Remove-ProvTask](Remove-ProvTask/)
  * [Stop-ProvTask](Stop-ProvTask/)
  * [Switch-ProvTask](Switch-ProvTask/)
  * [Add-ProvTaskMetadata](Add-ProvTaskMetadata/)
  * [Remove-ProvTaskMetadata](Remove-ProvTaskMetadata/)
## Parameters

| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| TaskId | Specifies the task identifier to be returned. | false | false |  |
| Type | Specifies the type of task to be returned. | false | false |  |
| Active | Specifies whether currently running tasks only or completed tasks only are returned. | false | false |  |
| Metadata | Gets records with matching metadata entries.<br>The value being compared with is a concatenation of the key name, a colon, and the value. For example: -Metadata "abc:x*" matches records with a metadata entry having a key name of "abc" and a value starting with the letter "x". | false | false |  |
| Property | Specifies the properties to be returned. This is similar to piping the output of the command through Select-Object, but the properties are filtered more efficiently at the server. | false | false |  |
| ReturnTotalRecordCount | When specified, the cmdlet outputs an error record containing the number of records available. This error record is additional information and does not affect the objects written to the output pipeline. See about_Prov_Filtering for details. | false | false | False |
| MaxRecordCount | Specifies the maximum number of records to return. | false | false | 250 |
| Skip | Skips the specified number of records before returning results. Also reduces the count returned by -ReturnTotalRecordCount. | false | false | 0 |
| SortBy | Sorts the results by the specified list of properties. The list is a set of property names separated by commas, semi-colons, or spaces. Optionally, prefix each name with a + or - to indicate ascending or descending order. Ascending order is assumed if no prefix is present. | false | false | The default sort order is by name or unique identifier. |
| Filter | Gets records that match a PowerShell-style filter expression. See about_Prov_Filtering for details. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller the PowerShell snap-in will connect to. You can provide this as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type
### 
   
## Return Values
### 
   ## Notes
   If the command fails, the following errors can result.<br>    Error Codes<br>    -----------<br>    UnknownObject<br>        One of the specified objects was not found.<br>    PartialData<br>         Only a subset of the available data was returned.<br>    InvalidFilter<br>        A filtering expression was supplied that could not be interpreted for this cmdlet.<br>    CouldNotQueryDatabase<br>         The query required to get the database was not defined.<br>    DatabaseError<br>        An error occurred in the service while attempting a database operation.<br>    DatabaseNotConfigured<br>        The operation could not be completed because the database for the service is not configured.<br>    DataStoreException<br>        An error occurred in the service while attempting a database operation - communication with the database failed for various reasons.<br>    PermissionDenied<br>        You do not have permission to execute this command.<br>    AuthorizationError<br>        There was a problem communicating with the Citrix Delegated Administration Service.<br>    CommunicationError<br>        There was a problem communicating with the remote service.<br>    ExceptionThrown<br>        An unexpected error occurred.  For more details, see the Windows event logs on the controller or the XenDesktop logs.
## Examples

### EXAMPLE 1
```
c:\PS>Get-ProvTask -Active $false

TaskId                   : cfe5b3a2-c471-443e-b05e-8658e672d10f
Type                     : MyTask
Host                     : NYSERVER
Status                   : Finished
CurrentOperation         :
TaskProgress             : 100
TaskExpectedCompletion   : 10/10/2012 15:28:12
LastUpdateTime           : 10/10/2012 15:28:12
ActiveElapsedTime        : 56
DateFinished             : 10/10/2012 15:28:12
TerminatingError         :
...
```
   Description<br>-----------<br>Get all completed tasks for the MachineCreation Service.<br>All tasks will publish at least the fields listed above, plus more related to the particular task being performed.
