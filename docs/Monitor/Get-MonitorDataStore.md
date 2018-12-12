
# Get-Monitordatastore
Gets details for each of the Monitor data stores.
## Syntax
```
Get-MonitorDataStore [-BearerToken <String>] [-AdminAddress <String>] [<CommonParameters>]
```
## Detailed Description
Returns an object for each of the Monitor data stores describing the connection string, data store name, db type, provider, schema name, and DB status.

A database connection must be configured in order for this command to be used if the service has a secondary data store. This is not required for the site data store.


## Related Commands

* [Reset-MonitorDataStore](./Reset-MonitorDataStore/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller the PowerShell snap-in will connect to. You can provide this as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type

### 

## Return Values

### Citrix.Monitor.Sdk.Datastoreconfiguration
An object describing the connection string, data store name, database type, provider, schema name and database status.
## Notes
If the command fails, the following errors can be returned.<br>    Error Codes<br>    -----------<br>    DatabaseError<br>        An error occurred in the service while attempting a database operation.<br>    DatabaseNotConfigured<br>        The operation could not be completed because the database for the service is not configured.<br>    DataStoreException<br>        An error occurred in the service while attempting a database operation - communication with the database failed for various reasons.<br>    PermissionDenied<br>        You do not have permission to execute this command.<br>    AuthorizationError<br>        There was a problem communicating with the Citrix Delegated Administration Service.<br>    CommunicationError<br>        There was a problem communicating with the remote service.<br>    ExceptionThrown<br>        An unexpected error occurred.  For more details, see the Windows event logs on the controller or the XenDesktop logs.
## Examples

### Example 1
```
c:\PS>Get-MonitorDataStore

ConnectionString : Server=.\SQLEXPRESS;Initial Catalog = databaseName; Integrated Security = True

DataStore        : Site

DatabaseType     : SqlServer

Provider         : MSSQL

SchemaName       : MonitorSiteSchema

Status           : OK

ConnectionString :

DataStore        : Secondary

DatabaseType     : SqlServer

Provider         : MSSQL

SchemaName       : MonitorSecondarySchema

Status           : DBUnconfigured
```
#### Description
Get the database connection string for the Monitor Service.
