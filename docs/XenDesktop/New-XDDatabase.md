
# New-Xddatabase
Creates the specified Database or all Databases.
## Syntax
```
New-XDDatabase -AllDefaultDatabases -DatabaseServer <String> -SiteName <String> [-DatabaseCredentials <PSCredential>] [-DatabaseNamePrefix <String>] [-AdminAddress <String>] [<CommonParameters>]

New-XDDatabase -DatabaseServer <String> -DataStore <DataStore> -SiteName <String> [-DatabaseCredentials <PSCredential>] [-DatabaseName <String>] [-AdminAddress <String>] [<CommonParameters>]
```
## Detailed Description
If AllDefaultDatabases is specified, this cmdlet creates all databases using their default names on the specified SQL server. When used in this manner, the cmdlet need only be called once.

If DataStore is specified, this cmdlet creates the specified database on the specified SQL Server. When used in this manner, the cmdlet should be called once per datastore.

This cmdlet creates, but does not configure, the Database. Run New-XDSite to configure the Site to use the Database.

For database mirroring please refer to "about\_XenDesktopModule\_SiteConfiguration".


## Related Commands

* [Get-XDDatabaseSchema](./Get-XDDatabaseSchema/)
* [Get-XDSite](./Get-XDSite/)
* [New-XDSite](./New-XDSite/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| AllDefaultDatabases | All databases are created with their default names. The default names are listed with their corresponding dataStore types as follows:<br>-- Site<br>The Site Configuration Database. The default name of this database is Citrix&lt;SiteName&gt;.<br>-- Logging<br>The Configuration Logging Database. The default name of this database is CitrixConfigLogging&lt;SiteName&gt;.<br>-- Monitor<br>The Monitoring Database. The default name of this database is CitrixMonitor&lt;SiteName&gt;. | true | false |  |
| DatabaseServer | The address of the SQL Server in which the database is to be created. This must include the SQL Instance name. | true | false |  |
| SiteName | The name of the Site for which the specified database is to be created. | true | false |  |
| DataStore | The datastore type that is to be created.  Valid values are Site, Logging and Monitor. | true | false |  |
| DatabaseCredentials | The security credentials, in the form of a PSCredential object, that will be used to connect to the SQL Server specified by the DatabaseServer parameter. If this parameter is not provided, then the implicit credentials of the user running the cmdlet are used to connect to the SQL Server. | false | false |  |
| DatabaseNamePrefix | The prefix to be added to the default database names when AllDefaultDatabases is specified. | false | false |  |
| DatabaseName | The name that should be used for the database of the specified datastore type. | false | false | Site = Citrix&lt;SiteName&gt;, Logging = CitrixConfigLogging&lt;SiteName&gt; and Monitor = CitrixMonitor&lt;SiteName&gt; |
| AdminAddress | Specifies the address of the Delivery Controller to which the PowerShell module will connect. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |

## Input Type

### None
You cannot pipe input into this cmdlet.
## Return Values

### Citrix.Xendesktoppowershellsdk.Serviceinterfaces.Configuration.Database
One Database object is returned for each datastore type that is created.  Each Database object includes the database name, datastore type and SQL Server address.
## Notes
If the user running this cmdlet does not have privilege to create databases on the specified SQL Server, then alternative credentials may be provided using the DatabaseCredentials parameter.<br>    The command can fail for the following reasons:<br>    o A connection could not be established with the specified SQL Server.<br>    o The person running the cmdlet, or the supplied credentials, do not have sufficient privilege to create databases on the specified SQL Server. In this situation, use Get-XDDatabaseSchema, instead of New-XDDatabase, to generate SQL database creation scripts that may be given to a database administrator for execution on the SQL Server.
## Examples

### Example 1
```
C:\PS> New-XDDatabase -AdminAddress MySiteController -SiteName MySite -Datastore Site -DatabaseServer MySqlServer\Instance_1 -DatabaseName MySiteDatabase
```
#### Description
Creates a Site Configuration Database called 'MySiteDatabase' for the Site named 'MySite' on 'Instance\_1' of the SQL Server 'MySqlServer'.
### Example 2
```
C:\PS> New-XDDatabase -AdminAddress MySiteController -SiteName MySite -Datastore Logging -DatabaseServer MySqlServer\Instance_1 -DatabaseName MyLoggingDatabase
```
#### Description
Creates a Configuration Logging Database called 'MyLoggingDatabase' for the Site named 'MySite' on 'Instance\_1' of the SQL Server 'MySqlServer'.
### Example 3
```
C:\PS> New-XDDatabase -AdminAddress MySiteController -SiteName MySite -Datastore Monitor -DatabaseServer MySqlServer\Instance_1 -DatabaseName MyMonitorDatabase
```
#### Description
Creates a Monitoring Database called 'MyMonitorDatabase' for the Site named 'MySite' on 'Instance\_1' of the SQL Server 'MySqlServer'.
### Example 4
```
C:\PS> New-XDDatabase -AdminAddress MySiteController -SiteName MySite -AllDefaultDatabases -DatabaseServer MySqlServer\Instance_1 -DatabaseNamePrefix  MyPrefix-
```
#### Description
Creates Site Configuration, Configuration Logging and Monitoring Databases called 'MyPrefix-CitrixMySite', 'MyPrefix-CitrixConfigLoggingMySite' and 'MyPrefix-CitrixMonitorMySite' for the Site named 'MySite' on 'Instance\_1' of the SQL Server 'MySqlServer'.
