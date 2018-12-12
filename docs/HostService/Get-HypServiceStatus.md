﻿# Get-HypServiceStatus

   Gets the current status of the Host Service on the controller.

## Syntax
```
Get-HypServiceStatus [-BearerToken <String>] [-AdminAddress <String>] [<CommonParameters>]
```

## Detailed Description
   Enables the status of the Host Service on the controller to be determined. The database connection to the service does not need to be configured before using this command.

## Related Commands
  * [Set-HypDBConnection](Set-HypDBConnection.html)
  * [Test-HypDBConnection](Test-HypDBConnection.html)
  * [Get-HypDBConnection](Get-HypDBConnection.html)
  * [Get-HypDBSchema](Get-HypDBSchema.html)
## Parameters

| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller the PowerShell snap-in will connect to. You can provide this as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type
### None
   You cannot pipe input into this cmdlet.
## Return Values
### Citrix.Fma.Sdk.Utilities.Service.ServiceStatusInfo
   The Get-HypServiceStatus command returns an object containing the status of the Host Service together with extra diagnostics information.<br>OK<br>    The Host Service is running and is connected to a database containing a valid schema.<br>DBUnconfigured<br>    The Host Service does not have a database connection configured.<br>DBRejectedConnection<br>    The database rejected the logon attempt from the Host Service.  This may be because the service attempted to log on with invalid credentials or because a database has not been installed in the specified location.<br>InvalidDBConfigured<br>    The expected stored procedures are missing from the database.  This may be because the Host Service schema has not been added to the database.<br>DBNotFound<br>    The specified database could not be located with the configured connection string.<br>DBMissingOptionalFeature<br>    The Host is connected to a database that is valid, but it does not have the full functionality required for optimal performance. Upgrading the database is advisable.<br>DBMissingMandatoryFeature<br>    The Host is connected to a database that is valid, but it does not have the full functionality required so the Host cannot function. Upgrading the database is required.<br>DBNewerVersionThanService<br>    The version of the Host Service currently in use is incompatible with the version of the Host Service schema on the database.  Upgrade the Host Service to a more recent version.<br>DBOlderVersionThanService<br>    The version of the Host Service schema on the database is incompatible with the version of the Host Service currently in use.  Upgrade the database schema to a more recent version.<br>DBVersionChangeInProgress<br>    A database schema upgrade is currently in progress.<br>PendingFailure<br>    Connectivity between the Host Service and the database has been lost. This may be a transitory network error, but may indicate a loss of connectivity that requires administrator intervention.<br>Failed<br>    Connectivity between the Host and the database has been lost for an extended period of time, or has failed due to a configuration problem. The Host service cannot operate while its connection to the database is unavailable.<br>Unknown<br>    (0) The service status cannot be determined.## Notes
   If the command fails, the following errors can be returned.<br>    Error Codes<br>    -----------<br>    DatabaseError<br>        An error occurred in the service while attempting a database operation.<br>    DatabaseNotConfigured<br>        The operation could not be completed because the database for the service is not configured.<br>    DataStoreException<br>        An error occurred in the service while attempting a database operation - communication with the database failed for various reasons.<br>    PermissionDenied<br>        You do not have permission to execute this command.<br>    AuthorizationError<br>        There was a problem communicating with the Citrix Delegated Administration Service.<br>    CommunicationError<br>        There was a problem communicating with the remote service.<br>    ExceptionThrown<br>        An unexpected error occurred.  For more details, see the Windows event logs on the controller or the XenDesktop logs.
## Examples

### EXAMPLE 1
```
C:\PS>Get-HypServiceStatus

DBUnconfigured
```
   Description<br>-----------<br>Get the current status of the Host Service.
