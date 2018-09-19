# Set-AppLibAppDisk

   Changes the parameter values for an AppDisk.

## Syntax
```
Set-AppLibAppDisk [-AppDiskName] <String> [-Description <String>] [-PassThru] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]

Set-AppLibAppDisk -AppDiskUid <Guid> [-Description <String>] [-PassThru] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
```

## Detailed Description
   Provides the ability to update the parameters of an existing AppDisk.

This allows the following parameters to be updated:

Description of the AppDisk.

To change the name of the AppDisk see Rename-AppLibAppDisk.

## Related Commands
  * [Get-AppLibAppDisk](Get-AppLibAppDisk/)
  * [Rename-AppLibAppDisk](Rename-AppLibAppDisk/)
## Parameters

| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| AppDiskName | The name of the AppDisk to be updated. | true | false |  |
| AppDiskUid | The identifier of the AppDisk to be updated. | true | false |  |
| Description | The description to apply; may be empty. | false | false |  |
| PassThru | Returns the affected record. By default, this cmdlet does not generate any output. | false | false | False |
| LoggingId | Specifies the identifier of the high-level operation this cmdlet call forms a part of. Citrix Studio and Director typically create high-level operations. PowerShell scripts can also wrap a series of cmdlet calls in a high-level operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller the PowerShell snap-in will connect to. You can provide this as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type
### 
   
## Return Values
### Citrix.AppLibrary.Sdk.AppDisk<br>          This object provides details of the AppDisk and contains the following information:<br>          AppDiskUid <Guid><br>          The unique identifier for the AppDisk.<br>          AppDiskName <string><br>          The name of the AppDisk.<br>          Description <string><br>          A description of the AppDisk.<br>          HostingUnitUid <Guid><br>          The unique identifier of the hosting unit (from the Hosting Unit PowerShell snap-in) that the scheme uses.<br>          HostingUnitName <string><br>          The name of the hosting unit (from the Hosting Unit PowerShell snap-in) that the scheme uses.<br>          VirtualDiskID <DateTime><br>          The MCS disk identifier for the AppDisk.<br>          TaskId <Guid><br>          The identifier of any current task that is running for the AppDisk.<br>          DiskLocalUid  <Guid><br>          The AppDNA identifier for the disk.<br>          DiskLocalVersion  <Guid><br>          The AppDNA version specifier for the disk.<br>          Scopes <ScopeReference[]><br>          The Delegated Administration scopes in which the AppDisk falls<br>          Task <Task<<br>          The state of any current task that is running for the AppDisk.<br>          State <AppDiskState><br>          The overall lifecycle state of the AppDisk<br>          StateString <string><br>          The overall lifecycle state of the AppDisk as a string<br>          AppDNAState <AppDNAState><br>          The AppDNA lifecycle state of the AppDisk<br>          AppDNAStateString <string><br>          The AppDNA lifecycle state of the AppDisk as a string<br>          NewVersionCreationInProgress <bool><br>          A value indicating whether a new version of this AppDisk is currently being created
   ## Notes
   In the case of failure, the following errors can result.<br>    Error Codes<br>    -----------<br>    AppDiskNotFound<br>    The specified AppDisk could not be located.<br>    DatabaseError<br>    An error occurred in the service while attempting a database operation.<br>    DatabaseNotConfigured<br>    The operation could not be completed because the database for the service is not configured.<br>    ServiceStatusInvalidDb<br>    An error occurred in the service while attempting a database operation - communication with the database failed<br>    for various reasons.<br>    CommunicationError<br>    An error occurred while communicating with the service.<br>    PermissionDenied<br>    The user does not have administrative rights to perform this operation.<br>    ConfigurationLoggingError<br>    The operation could not be performed because of a configuration logging error<br>    ExceptionThrown<br>    An unexpected error occurred.  To locate more details, see the Windows event logs on the controller being used or examine the XenDesktop logs.
## Examples

### EXAMPLE 1
```
C:\PS> Set-AppLibAppDisk -AppDiskName MyDisk -Description "Experimental"
```
   Description<br>-----------<br>Updates as AppDisk called "MyDisk" to have the description "Experimental".
