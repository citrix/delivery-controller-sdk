# Rename-AppLibAppDisk

   Renames a AppDisk.

## Syntax
```
Rename-AppLibAppDisk [-AppDiskName] <String> [-NewAppDiskName] <String> [-PassThru] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]

Rename-AppLibAppDisk -AppDiskUid <Guid> [-NewAppDiskName] <String> [-PassThru] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
```

## Detailed Description
   Provides the ability to change the name of an existing AppDisk.  The unique identifier for the AppDisk never changes after it has been created so, regardless of any name changes, the AppDisk can always be identified by its unique identifier.

## Related Commands
  * [New-AppLibAppDisk](New-AppLibAppDisk.html)
  * [Set-AppLibAppDisk](Set-AppLibAppDisk.html)
  * [Get-AppLibAppDisk](Get-AppLibAppDisk.html)
  * [Test-AppLibAppDiskNameAvailable](Test-AppLibAppDiskNameAvailable.html)
## Parameters

| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| AppDiskName | The current name of the AppDisk. | true | false |  |
| AppDiskUid | The identifier for the AppDisk that is to be renamed. | true | false |  |
| NewAppDiskName | The new name for the AppDisk.  This must be a name that is not being used by an existing AppDisk, and it must not contain any of the following characters \/;:#.*?=<>|[]()""' | true | false |  |
| PassThru | Defines whether or not the command returns a result showing the new state of the updated AppDisk. | false | false | true |
| LoggingId | Specifies the identifier of the high-level operation this cmdlet call forms a part of. Citrix Studio and Director typically create high-level operations. PowerShell scripts can also wrap a series of cmdlet calls in a high-level operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snap-in connects to.  You can provide this as a host name or an IP address. | false | false | LocalHost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type
### 
   
## Return Values
### Citrix.AppLibrary.Sdk.AppDisk<br>          This object provides details of the AppDisk and contains the following information:<br>          AppDiskUid <Guid><br>          The unique identifier for the AppDisk.<br>          AppDiskName <string><br>          The name of the AppDisk.<br>          Description <string><br>          A description of the AppDisk.<br>          HostingUnitUid <Guid><br>          The unique identifier of the hosting unit (from the Hosting Unit PowerShell snap-in) that the scheme uses.<br>          HostingUnitName <string><br>          The name of the hosting unit (from the Hosting Unit PowerShell snap-in) that the scheme uses.<br>          VirtualDiskID <DateTime><br>          The MCS disk identifier for the AppDisk.<br>          TaskId <Guid><br>          The identifier of any current task that is running for the AppDisk.<br>          DiskLocalUid  <Guid><br>          The AppDNA identifier for the disk.<br>          DiskLocalVersion  <Guid><br>          The AppDNA version specifier for the disk.<br>          Scopes <ScopeReference[]><br>          The Delegated Administration scopes in which the AppDisk falls<br>          Task <Task<<br>          The state of any current task that is running for the AppDisk.<br>          State <AppDiskState><br>          The overall lifecycle state of the AppDisk<br>          StateString <string><br>          The overall lifecycle state of the AppDisk as a string<br>          AppDNAState <AppDNAState><br>          The AppDNA lifecycle state of the AppDisk<br>          AppDNAStateString <string><br>          The AppDNA lifecycle state of the AppDisk as a string<br>          NewVersionCreationInProgress <bool><br>          A value indicating whether a new version of this AppDisk is currently being created
   ## Notes
   In the case of failure, the following errors can result.<br>    Error Codes<br>    -----------<br>    AppDiskNotFound<br>    The specified AppDisk could not be located.<br>    AppDiskNameAlreadyExists<br>    A AppDisk with the same name as the new AppDisk name already exists.<br>    DatabaseError<br>    An error occurred in the service while attempting a database operation.<br>    DatabaseNotConfigured<br>    The operation could not be completed because the database for the service is not configured.<br>    ServiceStatusInvalidDb<br>    An error occurred in the service while attempting a database operation - communication with the database failed<br>    for various reasons.<br>    CommunicationError<br>    An error occurred while communicating with the service.<br>    PermissionDenied<br>    The user does not have administrative rights to perform this operation.<br>    ConfigurationLoggingError<br>    The operation could not be performed because of a configuration logging error<br>    ExceptionThrown<br>    An unexpected error occurred.  To locate more details, see the Windows event logs on the controller being used or examine the XenDesktop logs.
## Examples

### EXAMPLE 1
```
C:\PS>Rename-AppLibAppDisk -AppDiskName CurrentName -NewAppDiskName NewName
```
   Description<br>-----------<br>Renames a AppDisk from "currentName" to "NewName".
### EXAMPLE 2
```
C:\PS>Rename-AppLibAppDisk -AppDiskName CurrentName -NewAppDiskName NewName -PassThru


          AppDiskUid             : 7585f0de-192e-4847-a6d8-22713c3a2f42
          AppDiskName            : NewName
          Description                 : Microsoft Office 2013
          MasterStorageID             : 03743136-e43b-4a87-af74-ab71686b3c16
          MasterDiskID                : c0571690-4f57-4476-901b-fe64d6aecb79
          HostingUnitUid              : 01a4a008-8ce8-4165-ba9c-cdf15a6b0501
          HostingUnitName             : HostUnit1
          TaskId                      : 00000000-0000-0000-0000-000000000000
          DiskLocalUid                : 4F8323D9-6978-4CA0-8231-22F9185C71B6
          DiskLocalVersion            : DDA81A28-6BF4-41E1-A120-67F72C164DF6
          Scopes                      :
```
   Description<br>-----------<br>Renames a AppDisk from "currentName" to "NewName" and displays the resulting state.
