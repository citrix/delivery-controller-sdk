
# New-Xdsite
Configures the databases for use with a new Site and initializes all of the associated Site services.
## Syntax
```
New-XDSite -AllDefaultDatabases -DatabaseServer <String> -SiteName <String> [-DatabaseMirrorServer <String>] [-DatabaseNamePrefix <String>] [-AdminAddress <String>] [<CommonParameters>]

New-XDSite -DatabaseServer <String> -LoggingDatabaseName <String> -MonitorDatabaseName <String> -SiteDatabaseName <String> -SiteName <String> [-DatabaseMirrorServer <String>] [-AdminAddress <String>] [<CommonParameters>]

New-XDSite -LoggingDatabaseName <String> -LoggingDatabaseServer <String> -MonitorDatabaseName <String> -MonitorDatabaseServer <String> -SiteDatabaseName <String> -SiteDatabaseServer <String> -SiteName <String> [-LoggingDatabaseMirrorServer <String>] [-MonitorDatabaseMirrorServer <String>] [-SiteDatabaseMirrorServer <String>] [-AdminAddress <String>] [<CommonParameters>]
```
## Detailed Description
Configures the Site for first use.  This must be run after the databases have been created. The databases may have been created manually using the scripts generated from Get-XDDatabaseSchema or automatically using New-XDDatabase.

The site will run in a grace period until Set-XDLicensing is used to configure licensing.

For database mirroring please refer to "about\_XenDesktopModule\_SiteConfiguration".


## Related Commands

* [Get-XDDatabaseSchema](./Get-XDDatabaseSchema/)
* [New-XDDatabase](./New-XDDatabase/)
* [Set-XDLicensing](./Set-XDLicensing/)
* [Get-XDSite](./Get-XDSite/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| AllDefaultDatabases | Indicates that all the databases that are to be used in this Site were created with their default names. | true | false |  |
| DatabaseServer | If all databases were created within a single SQL Server, this is the address of that server. This must include the SQL Instance name. | true | false |  |
| SiteName | The name of the Site that is to be created. | true | false |  |
| LoggingDatabaseName | If databases were not created using their default names, this is the name of the Configuration Logging Database. | true | false |  |
| MonitorDatabaseName | If databases were not created using their default names, this is the name of the Monitoring Database. | true | false |  |
| SiteDatabaseName | If databases were not created using their default names, this is the name of the Site Configuration Database. | true | false |  |
| LoggingDatabaseServer | If each database was created on a separate SQL Server, this is the name of the SQL Server hosting the Configuration Logging Database. This must include any applicable SQL Instance name. | true | false |  |
| MonitorDatabaseServer | If each database was created on a separate SQL Server, this is the name of the SQL Server hosting the Monitoring Database. This must include any applicable SQL Instance name. | true | false |  |
| SiteDatabaseServer | If each database was created on a separate SQL Server, this is the name of the SQL Server hosting the Site Configuration Database. This must include any applicable SQL Instance name. | true | false |  |
| DatabaseMirrorServer | If all databases were created within a single SQL Server and SQL Mirroring has been enabled for those databases, this is the address of the SQL Server that is acting as the Mirror. This must include the SQL Instance name. | false | false |  |
| DatabaseNamePrefix | If a name prefix was applied to the default database names during the original creation of the databases, this specifies that name prefix. | false | false |  |
| LoggingDatabaseMirrorServer | If each database was created on a separate SQL Server and SQL Mirroring has been enabled for the the Configuration Logging Database, this is the address of the SQL Server that is acting as the mirror. This must include any applicable SQL Instance name. | false | false | If this parameter is not provided, the mirror server is determined by querying the SQL Server hosting the Configuration Logging Database. |
| MonitorDatabaseMirrorServer | If each database was created on a separate SQL Server and SQL Mirroring has been enabled for the the Monitoring Database, this is the address of the SQL Server that is acting as the mirror. This must include any applicable SQL Instance name. | false | false | If this parameter is not provided, the mirror server is determined by querying the SQL Server that is hosting the Monitoring Database. |
| SiteDatabaseMirrorServer | If each database was created on a separate SQL Server and SQL Mirroring has been enabled for the the Site Configuration Database, this is the address of the SQL Server that is acting as the mirror. This must include any applicable SQL Instance name. | false | false | If this parameter is not provided, the mirror server is determined by querying the SQL Server that is hosting the Site Configuration Database. |
| AdminAddress | Specifies the address of the Delivery Controller to which the PowerShell module will connect. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |

## Input Type

### None
You cannot pipe input into this cmdlet.
## Return Values

### Citrix.Xendesktoppowershellsdk.Serviceinterfaces.Configuration.Site
This includes the name of the Site, the Delivery Controllers in Site, the Databases supporting the Site, the metadata associated with the Site, the licensing configuration of the Site, and the default Icon for the Site.
## Notes
The parameter set used with this cmdlet is dependent on the manner in which the databases were previously created.<br>    If the databases were created with default names on a single SQL Server, use the following parameter set:<br>    New-XDSite -AllDefaultDatabases -DatabaseServer &lt;String&gt; -SiteName &lt;String&gt; \[-DatabaseMirrorServer &lt;String&gt;\] \[-DatabaseNamePrefix &lt;String&gt;\] \[-AdminAddress &lt;String&gt;\]<br>    If the databases were created with non-default names on a single SQL Server, use the following parameter set:<br>    New-XDSite -DatabaseServer &lt;String&gt; -LoggingDatabaseName &lt;String&gt; -MonitorDatabaseName &lt;String&gt; -SiteDatabaseName &lt;String&gt; -SiteName &lt;String&gt; \[-DatabaseMirrorServer &lt;String&gt;\] \[-AdminAddress &lt;String&gt;\]<br>    If the databases were created on seperate SQL Servers, use the following parameter set:<br>    New-XDSite -LoggingDatabaseName &lt;String&gt; -LoggingDatabaseServer &lt;String&gt; -MonitorDatabaseName &lt;String&gt; -MonitorDatabaseServer &lt;String&gt; -SiteDatabaseName &lt;String&gt; -SiteDatabaseServer &lt;String&gt; -SiteName &lt;String&gt; \[-LoggingDatabaseMirrorServer &lt;String&gt;\] \[-MonitorDatabaseMirrorServer &lt;String&gt;\] \[-SiteDatabaseMirrorServer &lt;String&gt;\] \[-AdminAddress &lt;String&gt;\]<br>    The command can fail for the following reasons:<br>    o The Site associated with the Controller at AdminAddress is already configured.<br>    o One or more of the specified databases could not be found.<br>    o One or more of the specified databases does not have the necessary permissions for the Controller at AdminAddress.
## Examples

### Example 1
```
New-XDSite -AdminAddress MyController -AllDefaultDatabases -DatabaseServer MySqlServer\Instance_1 -SiteName MySite
```
#### Description
Configures a site called 'MySite' for the Controller 'MyController'.  All previously created databases have default names and are hosted on the SQL Server 'MySqlServer\\Instance\_1'.
### Example 2
```
New-XDSite -AdminAddress MyController -AllDefaultDatabases -DatabaseServer MySqlServer -DatabaseMirrorServer MySqlMirror -SiteName MySite
```
#### Description
Configures a site called 'MySite' for the Controller 'MyController'.  All previously created databases have default names, are hosted on the SQL Server 'MySqlServer' and mirrored on the SQL Server 'MySqlMirror'.
### Example 3
```
New-XDSite -AdminAddress MyController -AllDefaultDatabases -DatabaseServer MySqlServer -SiteName MySite -DatabaseNamePrefix MyPrefix-
```
#### Description
Configures a site called 'MySite' for the Controller 'MyController'.  All previously created databases have default names with a prefix of 'MyPrefix-' and are hosted on the SQL Server 'MySqlServer'.
### Example 4
```
New-XDSite -AdminAddress MyController -DatabaseServer MySqlServer -LoggingDatabaseName LoggingDb -MonitorDatabaseName MonitorDb -SiteDatabaseName SiteDb -SiteName MySite
```
#### Description
Configures a site called 'MySite' for the Controller 'MyController'.  The previously created databases have non-default names of 'LoggingDb' for the Configuration Logging Database, 'MonitorDb' for Monitoring Database and 'SiteDb' for the Site Configuration Database.  All databases are hosted on the SQL Server 'MySqlServer'.
### Example 5
```
New-XDSite -AdminAddress MyController -LoggingDatabaseName LoggingDb -LoggingDatabaseServer LoggingSqlServer -MonitorDatabaseName MonitorDb -MonitorDatabaseServer MonitorSqlServer -SiteDatabaseName SiteDb -SiteDatabaseServer SiteSqlServer -SiteName MySite
```
#### Description
Configures a site called 'MySite' for the Controller 'MyController'.&lt;br&gt;The previously created databases have non-default names and are hosted on individual SQL Servers. 'LoggingDb' and 'LoggingSqlServer 'for the Configuration Logging Database. 'MonitorDb' and 'MonitorSqlServer' for Monitoring Database. 'SiteDb' and 'SiteSqlServer' for the Site Configuration Database.
