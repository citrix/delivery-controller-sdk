# Remove-HypMetadata

   Removes metadata from a hypervisor connection or hosting unit.

## Syntax
```
Remove-HypMetadata [-LiteralPath] <String> [-Property <String>] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
```

## Detailed Description
   Use this command to remove custom data from a specific hosting unit or hypervisor connection.  If the Property parameter is not provided, all metadata is removed from the specified item.

## Related Commands
  * [Remove-HypMetadata](Remove-HypMetadata/)
## Parameters

| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| LiteralPath | Specifies the path within a Host Service provider to the hosting unit or hypervisor connection item from which to remove the metadata. The path specified must be in one of the following formats: <drive>:\HostingUnits\<HostingUnitName> or  <drive>:\HostingUnits\{<HostingUnit Uid> or  <drive>:\Connections\<Connection Name> or  <drive>:\Connections\{<Connection Uid>} | true | true (ByValue) |  |
| Property | Specifies the property name of the metadata to be removed. | false | false |  |
| LoggingId | Specifies the identifier of the high-level operation this cmdlet call forms a part of. Citrix Studio and Director typically create high-level operations. PowerShell scripts can also wrap a series of cmdlet calls in a high-level operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snap-in will connect to.  This can be provided as a host name or an IP address. | false | false | LocalHost. Once a value is provided by any cmdlet, this value will become the default. |

## Input Type
### System.string<br>    You can pipe a string that contains a path to Add-HypMetadata (Path parameter).
   
## Return Values
### 
   ## Notes
   In the case of failure, the following errors can result.<br>    Error Codes<br>    -----------<br>    InvalidPath<br>    The path provided is not in the required format.<br>    HostingUnitMetadataObjectToDeleteDoesNotExist<br>    The hosting unit supplied in the path does not exist.<br>    HypervisorConnectionObjectToDeleteDoesNotExist<br>    The hypervisor connection supplied in the path does not exist.<br>    MetadataContainerUndefined<br>    The specified path does not reference a hosting unit or a hypervisor connection.<br>    DatabaseError<br>    An error occurred in the service while attempting a database operation.<br>    DatabaseNotConfigured<br>    The operation could not be completed because the database for the service is not configured.<br>    DataStoreException<br>    An error occurred in the service while attempting a database operation - communication with the database failed for<br>    various reasons.<br>    CommunicationError<br>    An error occurred while communicating with the service.<br>    PermissionDenied<br>    The user does not have administrative rights to perform this operation.<br>    ExceptionThrown<br>    An unexpected error occurred.  To locate more details, see the Windows event logs on the controller being used or examine the XenDesktop logs.
## Examples

### EXAMPLE 1
```
C:\PS>Remove-HypMetadata -LiteralPath XDHyp:\Connections\MyConnection -Property MyProperty
```
   Description<br>-----------<br>The command removes the metadata with the property "MyProperty" from the hypervisor connection called "MyConnection".
### EXAMPLE 2
```
C:\PS>Remove-HypMetadata -LiteralPath XDHyp:\Connections\MyConnection
```
   Description<br>-----------<br>The command removes all the metadata from the hypervisor connection called "MyConnection".
### EXAMPLE 3
```
C:\PS>dir XDHyp:\connections | Remove-HypMetadata
```
   Description<br>-----------<br>The command removes all the metadata from all the hypervisor connections.
