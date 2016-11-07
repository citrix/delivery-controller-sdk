# Remove-AppLibAppVPackage

   Removes an App-V package from the library that is holding it

## Syntax
```
Remove-AppLibAppVPackage [-Uid] <Int32> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
```

## Detailed Description
   Provides the ability to remove an App-V package from the library that is holding it.

Removing a package from a library does not remove the whole reference to the package from the library, but rather marks it as not existing. Re-adding the package later will restore the reference. This cmdlet should only be used for removing packages from the manual library.

## Related Commands
## Parameters

| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| Uid | The App Library's internal unique identifier of the App-V package. | true | true (ByValue, ByPropertyName) |  |
| LoggingId | Specifies the identifier of the high-level operation this cmdlet call forms a part of. Citrix Studio and Director typically create high-level operations. PowerShell scripts can also wrap a series of cmdlet calls in a high-level operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller the PowerShell snap-in will connect to. You can provide this as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type
### 
   
## Return Values
### None
   ## Notes
   If the command fails, the following errors can result.<br>    Error Codes<br>    -----------<br>    UnknownObject<br>        No desktop group was found for the given uid. DatabaseError<br>        An error occurred in the service while attempting a database operation. DatabaseNotConfigured<br>        The operation could not be completed because the database for the service is not configured. DataStoreException<br>        An error occurred in the service while attempting a database operation - communication with the database failed for various reasons. PermissionDenied<br>        You do not have permission to execute this command. AuthorizationError<br>        There was a problem communicating with the Citrix Delegated Administration Service. CommunicationError<br>        There was a problem communicating with the remote service. ExceptionThrown<br>        An unexpected error occurred.  For more details, see the Windows event logs on the controller or the XenDesktop logs.
## Examples

### EXAMPLE 1
```
Remove-AppLibAppVPackage -Uid 5
```
   Description<br>-----------<br>Removes the specified package from the library that holds it by marking it as non- existing.
