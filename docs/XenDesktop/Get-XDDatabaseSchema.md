
# Get-Xddatabaseschema
Gets the SQL scripts used to create and manage the Database.
## Syntax
```
Get-XDDatabaseSchema -DatabaseServer <String> -DataStore <DataStore> -SiteName <String> [-DatabaseName <String>] [-ScriptType <DatabaseScriptType>] [-AdminAddress <String>] [<CommonParameters>]
```
## Detailed Description
Generates SQL scripts that can be given to a database administrator for execution. Scripts are written to standard output.

A script of type FullDatabase is used to manually create the Database with write access permissions for the Delivery Controller identified by AdminAddress. This script must be generated and executed for each datastore type supported by the Site.

Once the database administrator has executed all scripts of type FullDatabase, run New-XDSite to configure the databases for first use.


## Related Commands

* [New-XDDatabase](./New-XDDatabase/)
* [Add-XDController](./Add-XDController/)
* [Remove-XDController](./Remove-XDController/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| DatabaseServer | The address of the SQL server on which the generated script will be run. | true | false |  |
| DataStore | The datastore type of the script to be generated. There is no default value. Valid values are:<br>-- Site<br>This corresponds to the Site Configuration Database.<br>-- Logging<br>This corresponds to the Configuration Logging Database.<br>-- Monitor<br>This corresponds to the Monitor Database. | true | false |  |
| SiteName | The name of the Site for which the SQL script is to be generated. | true | false |  |
| DatabaseName | The name for the database of the selected datastore. There is a default name for each database. The default names are listed with their corresponding dataStore types as follows:<br>-- Site<br>The Site Configuration Database. The default name of this database is Citrix&lt;SiteName&gt;.<br>-- Logging<br>The Configuration Logging Database. The default name of this database is CitrixConfigLogging&lt;SiteName&gt;.<br>-- Monitor<br>The Monitoring Database. The default name of this database is CitrixMonitor&lt;SiteName&gt;. | false | false |  |
| ScriptType | The type of SQL script to be generated. By default, a script of type FullDatabase is generated. Valid types are:<br>-- AddController<br>This script is used to add a Controller specified by AdminAddress. It updates the specified database with all the access permissions needed by the Controller.<br>-- AddDatabaseLogOn<br>This script is used to add a logon for a Controller to the specified database server. It is used specifically for configuring SQL Server mirroring, in which the mirror database server must have appropriate logons created for all Controllers in the site.<br>-- FullDatabase<br>This script is used to create a database corresponding to the specified DataStore parameter. It also updates the database with all the access permissions needed for the Controller.<br>-- RemoveController<br>This script is used to remove a Controller specified by the ControllerToRemoveSid parameter. It removes the database access permissions previously required by the Controller. | false | false | FullDatabase |
| AdminAddress | Specifies the address of the Delivery Controller to which the PowerShell module will connect. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |

## Input Type

### None
You cannot pipe input into this cmdlet.
## Return Values

### System.String
A string containing the content of the generated SQL script.
## Notes
When the ScriptType is set to RemoveController, you must specify the dynamic parameter "ControllerToRemoveSid". This specifies the SID of the Controller that is to be removed from the Site. The resultant database script removes the controller's permissions to change the Database data.<br>    If a script of type FullDatabase is generated for a configured Site, the resulting script adds database access permissions for all known Controllers to the database to be created.<br>    If the cmdlet fails, the following error codes can result:<br>    o The datastore was not recognized.<br>    o The database server name could not be resolved.
## Examples

### Example 1
```
PS c:\> Get-XDDatabaseSchema -SiteName MySiteServiceGroup -DataStore Site -DatabaseName MySiteDB -DatabaseServer MyDBServer -ScriptType FullDatabase > c:\script.sql
```
#### Description
Gets the script for creating the Site Configuration Database and writes the content to the file "c:\\script.sql". This script may be executed on a database server "MyDBServer" for an existing and empty database with name "MySiteDB".
### Example 2
```
PS c:\> Get-XDDatabaseSchema -AdminAddress MyNewController -SiteName MySiteServiceGroup -DataStore Logging -DatabaseName MyLoggingDB -DatabaseServer MyDBServer -ScriptType AddController > c:\script.sql
```
#### Description
Gets the script used to write the access permissions for 'MyNewController' to the Configuration Logging Database. The contents of the script are written to the file "c:\\script.sql". This script may be executed on a database server "MyDBServer" for an existing database with name "MyLoggingDB". The Controller can then only be added to the Site by running Add-XDController.
### Example 3
```
PS c:\> Get-XDDatabaseSchema -SiteName MySiteServiceGroup -DataStore Monitor -DatabaseName MyMonitorDB -DatabaseServer MyDBServer -ScriptType RemoveController -ControllerToRemoveSid S-1-5-21-1234567890-123456789-123456789-1234 > c:\script.sql
```
#### Description
Gets the script used to remove the access permissions for a Controller with SID 'S-1-5-21-1234567890-123456789-123456789-1234' from the Monitoring Database. The contents of the script are written to the file "c:\\script.sql". This script can be executed only after the Controller has been removed from the Site with Remove-XDController. It may be executed on a database server "MyDBServer" for an existing database with name "MyLoggingDB".
### Example 4
```
PS c:\> Get-XDDatabaseSchema -AdminAddress MyExistingController -SiteName MySiteServiceGroup -DataStore Site -DatabaseName MySiteDB -DatabaseServer MyMirrorDBServer -ScriptType AddDatabaseLogOn > c:\script.sql
```
#### Description
Gets the script used to add a logon for 'MyExistingController' to the Site Configuration Database for the database mirror server "MyMirrorDBServer". The contents of the script are written to the file "c:\\script.sql".
