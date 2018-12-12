
# Get-Provvirtualdiskpendingoperation
Gets the operations queued for Virtual Disks.
## Syntax
```
Get-ProvVirtualDiskPendingOperation [-Id <Guid>] [-ReturnTotalRecordCount] [-MaxRecordCount <Int32>] [-Skip <Int32>] [-SortBy <String>] [-Filter <String>] [-BearerToken <String>] [-AdminAddress <String>] [<CommonParameters>]
```
## Detailed Description
Provides the ability to obtain a list of the operations queued for Virtual Disks.


## Related Commands

* [Get-ProvVirtualDisk](./Get-ProvVirtualDisk/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| Id | The identifier for the operation | false | false |  |
| ReturnTotalRecordCount | When specified, the cmdlet outputs an error record containing the number of records available. This error record is additional information and does not affect the objects written to the output pipeline. See about\_Prov\_Filtering for details. | false | false | False |
| MaxRecordCount | Specifies the maximum number of records to return. | false | false | 250 |
| Skip | Skips the specified number of records before returning results. Also reduces the count returned by -ReturnTotalRecordCount. | false | false | 0 |
| SortBy | Sorts the results by the specified list of properties. The list is a set of property names separated by commas, semi-colons, or spaces. Optionally, prefix each name with a + or - to indicate ascending or descending order. Ascending order is assumed if no prefix is present. | false | false | The default sort order is by name or unique identifier. |
| Filter | Gets records that match a PowerShell-style filter expression. See about\_Prov\_Filtering for details. | false | false |  |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller the PowerShell snap-in will connect to. You can provide this as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type

### 

## Return Values

### Citrix.Machinecreation.Sdk.Pendingvirtualdiskoperation
The object has the following properties:<br>OperationId &lt;Guid&gt; The unique identifier of the operation VirtualDiskId &lt;Guid&gt; The unique identifier for the virtual disk StorageId &lt;string&gt; The storage location on the hypervisor where the disk resides InProgress &lt;Boolean&gt; Whether the operation is in progress Progress &lt;int&gt; Percentage progress indication IsPriority &lt;Boolean&gt; Whether the operation is high priority OperationType &lt;string&gt; The kind of operation.  Currently the only valid value is "Replicate" TimeLastQueued  &lt;DateTime&gt; The date and time the operation was last queued for action LastErrorReported &lt;string&gt; The last reported error, if any Retries  &lt;int&gt; The number of times the operation has been retried.
## Notes
In the case of failure, the following errors can result.<br>    Error Codes<br>    -----------<br>    PartialData<br>    Only a subset of the available data was returned.<br>    CouldNotQueryDatabase<br>    The query required to get the database was not defined.<br>    PermissionDenied<br>    The user does not have administrative rights to perform this operation.<br>    ConfigurationLoggingError<br>    The operation could not be performed because of a configuration logging error<br>    CommunicationError<br>    An error occurred while communicating with the service.<br>    DatabaseNotConfigured<br>    The operation could not be completed because the database for the service is not configured.<br>    InvalidFilter<br>    A filtering expression was supplied that could not be interpreted for this cmdlet.<br>    ExceptionThrown<br>    An unexpected error occurred.  To locate more details, see the Windows event logs on the controller being used or examine the XenDesktop logs.
## Examples

### Example 1
```
C:\PS>Get-ProvVirtualDiskPendingOperation -Id "33ad07a7-edd7-589b-716a-86cad4739f5e"

          OperationId             : 33ad07a7-edd7-589b-716a-86cad4739f5e

          VirtualDiskId           : 5135a865-ba49-4e5f-87f2-2d65ee7a4e51

          StorageId               : a830de93-ddc5-b763-dc1a-35580a31401c

          InProgress              : False

          Progress                : 100

          IsPriority              : False

          OperationType           : Replicate

          TimeLastQueued          : 08/12/2012 09:35:30

          LastErrorReported       :

          Retries                 : 1
```
#### Description
Gets the operation '33ad07a7-edd7-589b-716a-86cad4739f5e'.
