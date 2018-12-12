
# about\_XenDesktopModule\_SiteConfiguration

## Topic
XenDesktop PowerShell Module - Site Configuration


## Short Description
Describes how to do the initial configuration of a Site using the XenDesktop PowerShell Module.


## Command Prefix
All commands in this module have 'XD' in their name.


## Long Description
After installing XenDesktop for the first time, the Site must be configured. Site configuration involves:


* Creating the databases that will be used by the Site.

* Instructing the various XenDesktop services to use the databases and making those services aware of each other.

* Licensing the Site and specifying which edition of XenDesktop to use.

Additional Delivery Controllers may be added to the Site once the initial configuration is complete.


### Database Creation
There is one main database, namely the Site Configuration Database, and two secondary databases, namely the Configuration Logging Database and the Monitoring Database.  These databases may be hosted on the same SQL Server or on dedicated SQL Servers.

The method used to create the databases depends on the SQL Server permissions held by the person configuring the Site, whether or not the databases use default names, and whether or not the databases are hosted on the same SQL Server.

If the person configuring the Site does not have sufficient privilege to create databases and add database logons in the SQL Server, then database creation is a two-stage process:


* Use the Get-XDDatabaseSchema cmdlet to generate one or more SQL scripts that contain commands to create the databases and configure SQL logons.

* The scripts must be executed by a database administrator with suitable privileges on the target SQL Server(s).

If the person configuring the Site has sufficient privilege, database creation is a single-stage process in which the New-XDDatabase cmdlet is used to create the databases and configure SQL logons.

When non-default database names are to be used, or the databases are to be hosted on individual SQL Servers, you must run either Get-XDDatabaseSchema or New-XDDatabase cmdlets once for each database.


### Database Mirroring
There are two variations of the New-XDDatabase cmdlet:


* One that is intended for Proof of concept and basic deployments. This variation is defined by the -AllDefaultDatabases switch parameter.

* The other is used to configure a database for each data store (Site, Logging, and Monitoring) individually. Each data store can be configured on different database server with different levels of access (user credentials). It is on these environments that mirroring is expected to be configured because mirroring can be targeted at a specific datastore. For instance; it may be considered that mirroring is not important for the monitoring data store.

When New-XDDatabase is to be used to configure each data store separately an empty database should be created on the database server with mirroring enabled before running New-XDDatabase. The empty database must have a collation which ends with "\_CI\_AS\_KS". In general, it is best to use a collation which ends with "\_100\_CI\_AS\_KS ". Once the databases have been configured for mirroring call New-XDDatabase for each data store (See the -DataStore parameter) and supply the principle database server address, the database credentials and the database name. New-XDDatabase will just populate the empty database if it sees that it is there. The mirror server address will be detected automatically and login scripts uploaded to the mirror server to allow the XenDesktop services access to the mirror database upon failover.

If using the "-AllDefaultDatabases" parameter set of these cmdlets the database names will not be known to the user upfront. Mirroring will need to be configured on the databases after they have been created using New-XDDatabase. New-XDDatabase will return information about the database names once it has completed. To configure mirroring on the databases; go to the SQL server and configure mirroring on the databases in the usual way. The mirror server will also need updating to allow XenDesktop access upon failover. To do this call:

"Get-XDDatabaseSchema -ScriptType AddDatabaseLogOn -DataStore ..."

for each datastore. Append the returned scripts together and upload the scripts to the mirror server. If this step is not performed XenDesktop will not be able to connect to the mirror server. The mirror server address can then be supplied to New-XDSite.

The databases can be created entirely via a manual process too. In which case New-XDDatabse will not be used. Instead call:

"Get-XDDatabaseSchema -ScriptType FullDatabase -DataStore ..."

for each data store and upload the resultant script to the database on the principle database server. Configure mirroring on the database if required and call:

"Get-XDDatabaseSchema -ScriptType AddDatabaseLogOn -DataStore ..."

and upload the resultant script to the mirror server. This will allow XenDesktop access to the server upon failover.

Once the databases have been created and populated call New-XDSite and supply the full information (Database Name, Database Server Address, and Database Mirror Server Address) for each data store.


### Service Initialization
During service initialization the XenDesktop services are instructed to use the databases, Configuration Logging is started and a temporary license is automatically enabled using the New-XDSite cmdlet.  If SQL Mirroring is enabled for the databases, the services are also made aware of the SQL Mirror Servers.

The site will run in a grace period until Set-XDLicensing is used to configure licensing.

There are three variations of the New-XDSite cmdlet to handle the following scenarios:


* The databases were created with default names on a single SQL Server.

* The databases were created with non-default names on a single SQL Server.

* The databases were created on individual SQL Servers.

### Licensing

The product edition and licensing model of the Site must be set, and details of a Citrix License Server from which licenses can be obtained must be provided.  Licensing must be set after running New-XDSite. Use the Set-XDLicensing cmdlet.


### Adding Controllers
The method used to add a Controller to an existing Site depends on the SQL Server permissions held by the person adding the Controller.

If the person adding the Controller does not have sufficient privilege to alter content of the databases and add database logons, then Controller addition is a three-stage process:


* The Get-XDDatabaseSchema cmdlet is used to generate one or more SQL scripts that contain commands to alter database content and configure SQL logons.

* The scripts must be executed by a database administrator with suitable privileges on the target SQL Server(s).

* After the scripts have been executed, the Add-XDController cmdlet is used with the DoNotUpdateDatabaseServer switch to configure the XenDesktop services on the new Controller.

If the person adding the Controller has sufficient privilege, the Add-XDController cmdlet is used without the DoNotUpdateDatabaseServer switch to alter database content, configure SQL logons and configure the XenDesktop services on the new Controller.


### Removing Controllers
The method used to remove a Controller from a Site depends on the SQL Server permissions held by the person removing the Controller.

If the person removing the Controller does not have sufficient privilege to alter content of the databases and remove database logons, then Controller removal is a three-stage process:


* Use the Remove-XDController cmdlet with the DoNotUpdateDatabaseServer switch to decommission the XenDesktop services on the Controller that is to be removed.

* Use the Get-XDDatabaseSchema cmdlet to generate one or more SQL scripts that contain commands to alter database content and remove SQL logons.

* Execute the scripts on the target SQL Server(s). This must be done by a database administrator with suitable privileges.

If the person removing the Controller has sufficient privilege, the Remove-XDController cmdlet is used without the DoNotUpdateDatabaseServer switch to decommission the XenDesktop services on the new Controller, alter database content and remove SQL logons.

Once a Controller has been removed from a Site, that Controller may be retired or added to another Site.


### Changing Secondary Databases

This may be required when, for example, the data contained in the Monitoring Database has grown to such an extent that a dedicated SQL Server is needed. The method required to change the name of one of the secondary databases that supports Configuration Logging and Monitoring, or the SQL Server hosting one of those databases, depends on the SQL Server permissions held by the person changing the database.

If the person changing a secondary database does not have sufficient privilege to create databases in the SQL Server hosting the new secondary databases and add database logons, then modification is a three-stage process:


  * Use the Get-XDDatabaseSchema cmdlet to generate an SQL script that contains commands to create the secondary database and configure SQL logons.

  * Execute the script on the target SQL Server. This must be done by a database administrator with suitable privileges.

  * After executing the script, use the Set-XDLogging and/or Set-XDMonitor cmdlets to configure the XenDesktop services in the Site to use the new secondary databases.

    If the person changing a secondary database has sufficient privilege to create databases in the SQL Server hosting the new secondary databases and add database logons, then:

  * Use the New-XDDatabase cmdlet to create the secondary databases and configure SQL logons.

  * Use the Set-XDLogging and/or Set-XDMonitor cmdlets to configure the XenDesktop services in the Site to use the new secondary databases.

## Examples


### Single Sql Server With Default Database Names, Sql Admin Access And No Sql

### Mirroring

    You have full administrative rights on the SQL Server 'SqlServer1' with instance 'SQLEXPRESS' and want to create a Site called 'Site1' and associate it with the Controller at 'Controller1'. Your Citrix License Server is listening on the default port (27000) of server CitrixLicenseServer.

```
    # Create the databases 
    C:\PS>  New-XDDatabase -AdminAddress Controller1 -DatabaseServer  
    SqlServer1\SQLEXPRESS -AllDefaultDatabases -SiteName Site1 

```

```
    # Create the Site 
    C:\PS> New-XDSite -AdminAddress Controller1 -DatabaseServer  
    SqlServer1\SQLEXPRESS -AllDefaultDatabases -SiteName Site1 

```

```
    # Set licensing 
    C:\PS> Set-XDLicensing -AdminAddress Controller1 -LicenseServerAddress  
    CitrixLicenseServer 

```

### Create A Site Using A Single Sql Server With Default Database Names, Sql Admin

### Access And Sql Mirroring
    You have full administrative rights on the SQL Server 'SqlServer1' with instance 'Instance1' and want to create a Site called 'Site1' and associate it with the Controller at 'Controller1'.  You want to configure the databases for SQL Server Mirroring using 'SqlMirror1' with 'Instance1'. Your Citrix License Server is listening on the non default port 27001 of server CitrixLicenseServer.

```
    # Create the databases 
    C:\PS>  New-XDDatabase -AdminAddress Controller1 -DatabaseServer  
    SqlServer1\Instance1 -AllDefaultDatabases -SiteName Site1 

```

```
    # Configure your SQL Server Mirror in the normal manner to mirror the three 
    # default databases  
    # 
    #
```

```
    # Create the Site and provide the mirror information 
    C:\PS> New-XDSite -AdminAddress Controller1 -DatabaseServer  
    SqlServer1\Instance1 -DatabaseMirrorServer SqlMirror1\Instance1  
    -AllDefaultDatabases -SiteName Site1 

```

```
    # Set licensing 
    C:\PS> Set-XDLicensing -AdminAddress Controller1 -LicenseServerAddress 
    CitrixLicenseServer -LicenseServerPort 27001 

```

### Create A Site Using A Single Sql Server With Default Database Names, Sql Admin

### Access Under Separate Username And No Sql Mirroring
    You have a separate user account with full administrative rights on the SQL Server 'SqlServer1' with instance 'SQLEXPRESS' and want to create a Site called 'Site1' and associate it with the Controller at 'Controller1'.  Your Citrix License Server is listening on the default port (27000) of server CitrixLicenseServer and you have a Platinum license.

```
    # Construct a Credential object for your SQL Administrator 
    C:\PS>  $cred = Get-Credential 

```

```
    # Create the databases 
    C:\PS>  New-XDDatabase -AdminAddress Controller1 -DatabaseServer  
    SqlServer1\SQLEXPRESS -DatabaseCredentials $cred -AllDefaultDatabases  
    -SiteName Site1 

```

```
    # Create the Site 
    C:\PS> New-XDSite -AdminAddress Controller1 -DatabaseServer  
    SqlServer1\SQLEXPRESS -AllDefaultDatabases -SiteName Site1 

```

```
    # Set licensing 
    C:\PS> Set-XDLicensing -AdminAddress Controller1 -LicenseServerAddress 
    CitrixLicenseServer -ProductEdition PLT 

```

### Create A Site Using A Single Sql Server With Non-Default Database Names, Sql

### Admin Access And No Sql Mirroring
    You have full administrative rights on the SQL Server 'SqlServer1' with instance 'SQLEXPRESS' and want to create a Site called 'Site1', associate it with the Controller at 'Controller1' and use database names of 'CitrixSiteDb', 'CitrixLoggingDb' and 'CitrixMonitorDb'.   Your Citrix License Server is listening on the default port (27000) of server CitrixLicenseServer and you have an Enterprise license.

```
    # Create the Site Database 
    C:\PS> New-XDDatabase -AdminAddress Controller1 -DataStore Site  
    -DatabaseServer SqlServer1\SQLEXPRESS -DatabaseName CitrixSiteDb  
    -SiteName Site1 

```

```
    # Create the Logging Database 
    C:\PS> New-XDDatabase -AdminAddress Controller1 -DataStore Logging  
    -DatabaseServer SqlServer1\SQLEXPRESS -DatabaseName CitrixLoggingDb  
    -SiteName Site1 

```

```
    # Create the Monitor Database 
    C:\PS> New-XDDatabase -AdminAddress Controller1 -DataStore Monitor 
    -DatabaseServer SqlServer1\SQLEXPRESS -DatabaseName CitrixMonitorDb 
    -SiteName Site1 

```

```
    # Create the Site 
    C:\PS> New-XDSite -AdminAddress Controller1 -DatabaseServer  
    SqlServer1\SQLEXPRESS -SiteDatabaseName CitrixSiteDb -LoggingDatabaseName 
    CitrixLoggingDb -MonitorDatabaseName CitrixMonitorDb -SiteName Site1 

```

```
    # Set licensing 
    C:\PS> Set-XDLicensing -AdminAddress Controller1 -LicenseServerAddress 
    CitrixLicenseServer -ProductEdition ENT 

```

### Create A Site Using One Sql Server Per Database With Non-Default Database

### Names, Sql Admin Access And No Sql Mirroring
    You have full administrative rights on the SQL Servers 'SqlServerSite', 'SqlServerLogging' and 'SqlServerMonitor'  with instance 'SQLEXPRESS' on each SQL Server. You want to create a Site called 'Site1', associate it with the Controller at 'Controller1' and use database names of 'CitrixSiteDb', 'CitrixLoggingDb' and 'CitrixMonitorDb'. Your Citrix License Server is listening on the default port (27000) of server CitrixLicenseServer and you have a Platinum license.

```
    # Create the Site Database 
    C:\PS> New-XDDatabase -AdminAddress Controller1 -DataStore Site  
    -DatabaseServer SqlServerSite\SQLEXPRESS -DatabaseName CitrixSiteDb 
    -SiteName Site1 

```

```
    # Create the Logging Database 
    C:\PS> New-XDDatabase -AdminAddress Controller1 -DataStore Logging 
    -DatabaseServer SqlServerLogging\SQLEXPRESS -DatabaseName CitrixLoggingDb 
    -SiteName Site1 

```

```
    # Create the Monitor Database 
    C:\PS> New-XDDatabase -AdminAddress Controller1 -DataStore Monitor 
    -DatabaseServer SqlServerMonitor\SQLEXPRESS -DatabaseName CitrixMonitorDb 
    -SiteName Site1 

```

```
    # Create the Site 
    C:\PS> New-XDSite -AdminAddress Controller1 -SiteDatabaseServer  
    SqlServerSite\SQLEXPRESS -SiteDatabaseName CitrixSiteDb  
    -LoggingDatabaseServer SqlServerLogging\SQLEXPRESS -LoggingDatabaseName  
    CitrixLoggingDb -MonitorDatabaseServer SqlServerMonitor\SQLEXPRESS  
    -MonitorDatabaseName CitrixMonitorDb -SiteName Site1 

```

```
    # Set licensing 
    C:\PS> Set-XDLicensing -AdminAddress Controller1 -LicenseServerAddress 
    CitrixLicenseServer -ProductEdition PLT 

```

### Create A Site Using One Sql Server Per Database With Non-Default Database

### Names, Sql Admin Access And Sql Mirroring
    You have full administrative rights on the SQL Servers 'SqlServerSite', 'SqlServerLogging' and 'SqlServerMonitor'  with instance 'Instance1' on each SQL Server. You want to create a Site called 'Site1', associate it with the Controller at 'Controller1' and use database names of 'CitrixSiteDb', 'CitrixLoggingDb' and 'CitrixMonitorDb'. You also want to configure the databases for SQL Server Mirroring using 'SqlMirrorSite', 'SqlMirrorLogging' and 'SqlMirrorMonitor' with instance 'Instance1'. Your Citrix License Server is listening on the default port (27000) of server CitrixLicenseServer and you have a Platinum license.

```
    # Create the empty databases for each data store and configure mirroring 
    # on those databases. 
    # 
    #
```

```
    # Populate the Site Database 
    C:\PS> New-XDDatabase -AdminAddress Controller1 -DataStore Site  
    -DatabaseServer SqlServerSite\Instance1 -DatabaseName CitrixSiteDb  
    -SiteName Site1 

```

```
    # Populate the Logging Database 
    C:\PS> New-XDDatabase -AdminAddress Controller1 -DataStore Logging  
    -DatabaseServer SqlServerLogging\Instance1 -DatabaseName CitrixLoggingDb  
    -SiteName Site1 

```

```
    # Populate the Monitor Database 
    C:\PS> New-XDDatabase -AdminAddress Controller1 -DataStore Monitor  
    -DatabaseServer SqlServerMonitor\Instance1 -DatabaseName CitrixMonitorDb  
    -SiteName Site1 

```

```
    # Create the Site 
    C:\PS> New-XDSite -AdminAddress Controller1 -SiteDatabaseServer  
    SqlServerSite\Instance1 -SiteDatabaseMirrorServer SqlMirrorSite\Instance1  
    -SiteDatabaseName CitrixSiteDb -LoggingDatabaseServer  
    SqlServerLogging\Instance1 -LoggingDatabaseMirrorServer  
    SqlMirrorLogging\Instance1 -LoggingDatabaseName CitrixLoggingDb  
    -MonitorDatabaseServer SqlServerMonitor\Instance1  
    -MonitorDatabaseMirrorServer SqlMirrorMonitor\Instance1  
    -MonitorDatabaseName CitrixMonitorDb -SiteName Site1 

```

```
    # Set licensing 
    C:\PS> Set-XDLicensing -AdminAddress Controller1 -LicenseServerAddress 
    CitrixLicenseServer -ProductEdition PLT 

```

### Create A Site Using A Single Sql Server With Non-Default Database Names, No

### Sql Admin Access And No Sql Mirroring
    You have no administrative rights on the SQL Server 'SqlServer1' with instance 'SQLEXPRESS' and want to create a Site called 'Site1', associate it with the Controller at 'Controller1' and use database names of 'CitrixSiteDb', 'CitrixLoggingDb' and 'CitrixMonitorDb'. Your Citrix License Server is listening on the default port (27000) of server CitrixLicenseServer and you have a Platinum license.

```
    # Get the SQL script to create the Site Database 
    C:\PS> Get-XDDatabaseSchema -AdminAddress Controller1 -DataStore Site 
    -DatabaseServer SqlServer1\SQLEXPRESS -DatabaseName CitrixSiteDb -SiteName  
    Site1 -ScriptType FullDatabase > C:\siteScript.sql 

```

```
    # Get the SQL script to create the Logging Database 
    C:\PS> Get-XDDatabaseSchema -AdminAddress Controller1 -DataStore Logging  
    -DatabaseServer SqlServer1\SQLEXPRESS -DatabaseName CitrixLoggingDb  
    -SiteName Site1 -ScriptType FullDatabase > C:\LoggingScript.sql 

```

```
    # Get the SQL script to create the Monitor Database 
    C:\PS> Get-XDDatabaseSchema -AdminAddress Controller1 -DataStore Monitor  
    -DatabaseServer SqlServer1\SQLEXPRESS -DatabaseName CitrixMonitorDb  
    -SiteName Site1 -ScriptType FullDatabase > C:\monitorScript.sql 

```

```
    # Get an individual with suitable privileges to execute the SQL scripts  
    # 'siteScript.sql', 'loggingScript.sql' and 'monitorScript.sql'on  
    # 'SqlServer1' 
    # 
    #
```

```
    # Create the Site 
    C:\PS> New-XDSite -AdminAddress Controller1 -DatabaseServer  
    SqlServer1\SQLEXPRESS -SiteDatabaseName CitrixSiteDb -LoggingDatabaseName  
    CitrixLoggingDb -MonitorDatabaseName CitrixMonitorDb -SiteName Site1 

```

```
    # Set licensing 
    C:\PS> Set-XDLicensing -AdminAddress Controller1 -LicenseServerAddress 
    CitrixLicenseServer -ProductEdition PLT 

```

### Determine Applicable Licensing Models And Product Editions
    You want to determine the license models and product editions that are applicable to your XenDesktop installation.

```
    # Determine your product code 
    C:\PS> $site = Get-XDSite 
    C:\PS> $productCode = $site.LicenseInformation.ProductCode 

```

```
    # Load the Citrix.Configuration.Admin.V2 snapin, as this exposes cmdlets to  
    # retrieve the licensing models and product editions 
    C:\PS> Add-PSSnapin Citrix.Configuration.Admin.V2 

```

```
    # Get the applicable licensing models 
    C:\PS> Get-ConfigLicensingModel -ProductCode $productCode 

```

```
    # Get the applicable product editions 
    C:\PS> Get-ConfigProductEdition -ProductCode $productCode 

```

### Change The Configuration Logging Database
    You have full administrative rights on the SQL Server 'SqlServer2' with instance 'INSTANCE1'  and want to change Configuration Logging for site 'Site1' to use a new database called 'CitrixLoggingDb\_New' on that server.

```
    # Create the Configuration Logging Database on the new SQL Server 
    C:\PS> New-XDDatabase -Datastore Logging -SiteName Site1 -DatabaseServer  
    SqlServer2\INSTANCE1 -DatabaseName CitrixLoggingDb_New 

```

```
    # Change Configuration Logging to use the new database 
    C:\PS> Set-XDLogging -DatabaseServer SqlServer2\INSTANCE1 -DatabaseName  
    CitrixLoggingDb_New 

```

### Change The Monitoring Database
    You have full administrative rights on the SQL Server 'SqlServer2' with instance 'INSTANCE1'  and want to change Monitoring for site 'Site1' to use a new database called 'CitrixMonitorDb\_New' on that server.

```
    # Create the Monitoring Database on the new SQL Server 
    C:\PS> New-XDDatabase -Datastore Monitor -SiteName Site1 -DatabaseServer  
    SqlServer2\INSTANCE1 -DatabaseName CitrixMonitorDb_New 

```

```
    # Change Monitoring to use the new database 
    C:\PS> Set-XDMonitor -DatabaseServer SqlServer2\INSTANCE -DatabaseName  
    CitrixMonitorDb_New 

```

### Add A Controller To A Site For Which You Have Full Db Admin
    You have full administrative rights on the SQL Server that underlies a Site called 'Site1'. An existing Controller in the Site is 'Controller1' and you want to add Controller 'AdditionalController' to the Site.

```
    C:\PS> Add-XDController -AdminAddress AdditionalController  
    -SiteControllerAddress Controller1 

```

### Add A Controller To A Site For Which You Have Full Db Admin Under Separate

### Username
    You have a separate user account with full administrative rights on the SQL Server that underlies a Site called 'Site1'. An existing Controller in the Site is 'Controller1' and you want to add Controller 'AdditionalController' to the Site.

```
    # Construct a Credential object for your SQL Administrator 
    C:\PS>  $cred = Get-Credential 

```

```
    # Add the Controller 
    C:\PS> Add-XDController -AdminAddress AdditionalController  
    -SiteControllerAddress Controller1 -DatabaseCredentials $cred 

```

### Add A Controller To A Site For Which You Have Full Db Admin Under Separate

### Usernames
    You have separate user accounts with full administrative rights on the three SQL Servers that underlie a Site called 'Site1'. An existing Controller in the Site is 'Controller1' and you want to add Controller 'AdditionalController' to the Site.

```
    # Construct a Credential object for your Site Database SQL Administrator 
    C:\PS>  $credSite = Get-Credential 

```

```
    # Construct a Credential object for your Logging Database SQL Administrator 
    C:\PS>  $credLogging = Get-Credential 

```

```
    # Construct a Credential object for your Monitor Database SQL Administrator 
    C:\PS>  $credMonitor = Get-Credential 

```

```
    # Add the Controller 
    C:\PS> Add-XDController -AdminAddress AdditionalController  
    -SiteControllerAddress Controller1 -SiteDatabaseCredentials $credSite  
    -LoggingDatabaseCredentials $credLogging -MonitorDatabaseCredentials  
    $credMonitor 

```

### Add A Controller To A Site For Which You Have No Db Admin Access
    You have no administrative rights on the SQL Server 'SqlServer1' with instance 'SQLEXPRESS' that underlies a Site called 'Site1'. The Site's databases are called 'CitrixSiteDb', 'CitrixLoggingDb' and 'CitrixMonitorDb'. An existing Controller in the Site is 'Controller1' and you want to add Controller 'AdditionalController' to the Site.

```
    # Get the SQL script that may be used to add permissions for  
    # 'AdditionalController' to the Site Database 
    C:\PS> Get-XDDatabaseSchema -AdminAddress Controller1 -DataStore Site  
    -DatabaseServer SqlServer1\SQLEXPRESS -DatabaseName CitrixSiteDb -SiteName  
    Site1 -ScriptType AddController > C:\siteScript.sql 

```

```
    # Get the SQL scripts that may be used to add permissions for ' 
    # AdditionalController' to the Logging Database 
    C:\PS> Get-XDDatabaseSchema -AdminAddress Controller1 -DataStore Logging  
    -DatabaseServer SqlServer1\SQLEXPRESS -DatabaseName CitrixLoggingDb  
    -SiteName Site1-ScriptType AddController > C:\loggingScript.sql 

```

```
    # Get the SQL script that may be used to add permissions for  
    # 'AdditionalController' to the Monitor Database 
    C:\PS> Get-XDDatabaseSchema -AdminAddress Controller1 -DataStore Monitor  
    -DatabaseServer SqlServer1\SQLEXPRESS -DatabaseName CitrixMonitorDb  
    -SiteName Site1-ScriptType AddController > C:\monitorScript.sql 

```

```
    # Get an individual with suitable privileges to execute the SQL scripts  
    # 'siteScript.sql', 'loggingScript.sql' and 'monitorScript.sql'on  
    # 'SqlServer1' 
    # 
    #
```

```
    # Add the Controller 
    C:\PS> Add-XDController -AdminAddress AdditionalController  
    -SiteControllerAddress Controller1 -DoNotUpdateDatabaseServer 

```

### Remove A Controller From A Site For Which You Have Full Db Admin Access
    You have full administrative rights on the SQL Server that underlies a Site called 'Site1'. The Site currently has two Controllers, namely 'Controller1' and 'RedundantController'. You want to remove 'RedundantController' from the Site.

```
    C:\PS> Remove-XDController -AdminAddress Controller1 -ControllerName  
    RedundantController 

```

### Remove A Controller From A Site For Which You Have Full Db Admin Under

### Separate Username
    You have a separate user account with full administrative rights on the SQL Server that underlies a Site called 'Site1'. The Site currently has two Controllers, namely 'Controller1' and 'RedundantController'. You want to remove 'RedundantController' from the Site.

```
    # Construct a Credential object for your SQL Administrator 
    C:\PS>  $cred = Get-Credential 

```

```
    # Remove the Controller 
    C:\PS> Remove-XDController -AdminAddress Controller1 -ControllerName  
    RedundantController -DatabaseCredentials $cred 

```

### Remove A Controller From A Site For Which You Have Full Db Admin Under

### Separate Usernames
    You have separate user accounts with full administrative rights on the three SQL Servers that underlie a Site called 'Site1'. The Site currently has two Controllers, namely 'Controller1' and 'RedundantController'. You want to remove 'RedundantController' from the Site.

```
    # Construct a Credential object for your Site Database SQL Administrator 
    C:\PS>  $credSite = Get-Credential 

```

```
    # Construct a Credential object for your Logging Database SQL Administrator 
    C:\PS>  $credLogging = Get-Credential 

```

```
    # Construct a Credential object for your Monitor Database SQL Administrator 
    C:\PS>  $credMonitor = Get-Credential 

```

```
    # Remove the Controller 
    C:\PS> Remove-XDController -AdminAddress Controller1 -ControllerName  
    RedundantController -SiteDatabaseCredentials $credSite  
    -LoggingDatabaseCredentials $credLogging -MonitorDatabaseCredentials  
    $credMonitor 

```

### Remove A Controller From A Site For Which You Have No Db Admin Access
    You have no administrative rights on the SQL Server 'SqlServer1' with instance 'SQLEXPRESS' that underlies a Site called 'Site1'. The Site's databases are called 'CitrixSiteDb', 'CitrixLoggingDb' and 'CitrixMonitorDb'. The Site currently has two Controllers, namely 'Controller1' and 'RedundantController'. You want to remove 'RedundantController' from the Site. 'RedundantController' is in the 'ACME' domain.

```
    # Determine the SID of the Controller that is to be removed. 
    C:\PS> $site = Get-XDSite 
    C:\PS> $redundantController = $site.Controllers  | Where-Object  
    {$_.MachineName -eq ' ACME\RedundantController '} 
    C:\PS> $redundantControllerSid = $redundantController.Sid 

```

```
    # Remove the Controller 
    C:\PS> Remove-XDController -AdminAddress Controller1 -ControllerName  
    RedundantController -DoNotUpdateDatabaseServer 

```

```
    # Get the SQL scripts that may be used to remove permissions for  
    # 'RedundantController' from the Site Database 
    C:\PS> Get-XDDatabaseSchema -AdminAddress Controller1 -DataStore Site  
    -DatabaseServer SqlServer1\SQLEXPRESS -DatabaseName CitrixSiteDb -SiteName  
    Site1 -ScriptType RemoveController -ControllerToRemove  
    $redundantControllerSid > C:\siteScript.sql 

```

```
    # Get the SQL script that may be used to remove permissions for ' 
    # RedundantController' from the Logging Database 
    C:\PS> Get-XDDatabaseSchema -AdminAddress Controller1 -DataStore Logging  
    -DatabaseServer SqlServer1\SQLEXPRESS -DatabaseName CitrixLoggingDb  
    -SiteName Site1-ScriptType RemoveController -ControllerToRemove  
    $redundantControllerSid > C:\loggingScript.sql 

```

```
    # Get the SQL script that may be used to remove permissions for  
    # 'RedundantController' from the Monitor Database 
    C:\PS> Get-XDDatabaseSchema -AdminAddress Controller1 -DataStore Monitor  
    -DatabaseServer SqlServer1\SQLEXPRESS -DatabaseName CitrixMonitorDb  
    -SiteName Site1-ScriptType RemoveController -ControllerToRemove  
    $redundantControllerSid > C:\monitorScript.sql 

```

```
    # Although not necessary, Citrix recommends you get an individual 
    # with suitable privileges to execute the SQL scripts 'siteScript.sql',  
    # 'loggingScript.sql' and 'monitorScript.sql'on 'SqlServer1' 
    #
```

## See Also

* [Get-XDDatabaseSchema](./Get-XDDatabaseSchema/)
* [New-XDDatabase](./New-XDDatabase/)
* [New-XDSite](./New-XDSite/)
* [Set-XDLicensing](./Set-XDLicensing/)
* [Add-XDController](./Add-XDController/)
* [Remove-XDController](./Remove-XDController/)
* [Set-XDLogging](./Set-XDLogging/)
* [Set-XDMonitor](./Set-XDMonitor/)

