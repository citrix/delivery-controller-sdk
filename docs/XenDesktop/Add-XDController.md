
# Add-Xdcontroller
Adds a Delivery Controller to an existing Site.
## Syntax
```
Add-XDController -DatabaseCredentials <PSCredential> -SiteControllerAddress <String> [-AdminAddress <String>] [<CommonParameters>]

Add-XDController -SiteControllerAddress <String> [-DoNotUpdateDatabaseServer] [-AdminAddress <String>] [<CommonParameters>]

Add-XDController -LoggingDatabaseCredentials <PSCredential> -MonitorDatabaseCredentials <PSCredential> -SiteDatabaseCredentials <PSCredential> -SiteControllerAddress <String> [-AdminAddress <String>] [<CommonParameters>]
```
## Detailed Description
Adds a Controller to an existing Site.

If no credentials are provided and DoNotUpdateDatabaseServer has not been specified, then all database update operations are attempted using the credentials of the user running the cmdlet.

If DatabaseCredentials is provided, then all database operations are attempted using those credentials.

If one or more of SiteDatabaseCredentials, LoggingDatabaseCredentials or MonitorDatabaseCredentials are provided, then all three must be provided. All operations are then attempted using the credentials appropriate to each Database.


## Related Commands

* [Get-XDDatabaseSchema](./Get-XDDatabaseSchema/)
* [Get-XDSite](./Get-XDSite/)
* [Remove-XDController](./Remove-XDController/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| DatabaseCredentials | The security credentials, in the form of a PSCredential object, that will be used to connect to the SQL Servers associated with the Site Configuration, Configuration Logging and Monitoring Databases. | true | false |  |
| LoggingDatabaseCredentials | The security credentials, in the form of a PSCredential object, that will be used to connect to the SQL Server associated with the Configuration Logging Database. | true | false |  |
| MonitorDatabaseCredentials | The security credentials, in the form of a PSCredential object, that will be used to connect to the SQL Server associated with the Monitoring Database. | true | false |  |
| SiteDatabaseCredentials | The security credentials, in the form of a PSCredential object, that will be used to connect to the SQL Server associated with the Site Configuration Database. | true | false |  |
| SiteControllerAddress | The address of a Controller in the Site to which this Controller is to be joined. | true | false |  |
| DoNotUpdateDatabaseServer | Results in the permissions associated with the Controller not being automatically added to the Database.<br>This switch may be useful when the person running the cmdlet does not have sufficient database privilege.  The database permissions for the Controller that is to be added must have been applied manually prior to running this cmdlet, otherwise the Controller is not added and an error is returned.<br>Get-XDDatabaseSchema may be used to generate the SQL script which in turn may be used to add the necessary permissions to the Database.<br>This parameter results in all supplied credentials being ignored. | false | false |  |
| AdminAddress | Specifies the address of the Delivery Controller to which the PowerShell module will connect. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |

## Input Type

### None
You cannot pipe input to this cmdlet.
## Return Values

### None

## Notes
In general, the AdminAddress specifies the Controller to which the PowerShell module will connect. However, in this cmdlet, not only is this the address of the Controller to connect to, it is also the Controller that is to be added to this Site.<br>    If the user running this cmdlet does not have privilege to add users to the Database, then use either the DoNotudpateDatabaseServer switch or supply alternative credentials using one or more of the Credential arguments.<br>    The command can fail for the following reasons:<br>    o The Controller is already a member of a Site.<br>    o The DoNotUpdateDatabaseServer parameter was specified, but the permissions for the Controller are not already in the Database. Either add the permissions using Get-XDDatabaseSchema or allow this cmdlet to add the permissions automatically.<br>    o The person running the cmdlet, or the supplied credentials, do not have sufficient privilege to update the Database. Either run this cmdlet as a user that has administrator privilege to the Database, or supply an account with suitable privileges using the PSCredential parameter(s).
## Examples

### Example 1
```
C:\PS> Add-XDController -AdminAddress MyNewController -SiteControllerAddress MyExistingController
```
#### Description
Adds the Controller 'MyNewController' to the Site to which 'MyExistingController' is already joined.  The permissions for 'MyNewController' will be added automatically to the Database using the implicit credentials of the user running the cmdlet.
### Example 2
```
C:\PS> Get-XDDatabaseSchema -AdminAddress MyNewController -SiteName MySite -DatabaseServer MySQLServer -ScriptType AddController > C:\addController.sql

C:\PS> # Get a database administrator to run addController.sql

C:\PS> Add-XDController -AdminAddress MyNewController -SiteControllerAddress MyExistingController -DoNotUpdateDatabaseServer
```
#### Description
Adds the Controller 'MyNewController' to the Site to which 'MyExistingController' is already joined.&lt;br&gt;The permissions for 'MyNewController' will not be added to the Database.  Instead the Get-XDDatabaseSchema cmdlet is used to generate a SQL script that must be given to the database administrator of 'MySQLServer'. The SQL script must be used to add the necessary permissions for 'MyNewController' before Add-XDController is run.
### Example 3
```
C:\PS> $credential = Get-Credential

C:\PS> Add-XDController -AdminAddress MyNewController -SiteControllerAddress MyExistingController -DatabaseCredentials $credential
```
#### Description
Adds the Controller 'MyNewController' to the Site to which 'MyExistingController' is already joined.&lt;br&gt;The credentials contained within '\$credential' will be used to add the necessary permissions for 'MyNewController' to the Database.
### Example 4
```
C:\PS> $credentialSite = Get-Credential

C:\PS> $credentialLogging = Get-Credential

C:\PS> $credentialMonitor = Get-Credential

C:\PS> Add-XDController -AdminAddress MyNewController -SiteControllerAddress MyExistingController -SiteDatabaseCredentials $credentialSite -LoggingDatabaseCredentials $credentialLogging -MonitorDatabaseCredentials $credentialMonitor
```
#### Description
Adds the Controller 'MyNewController' to the Site to which 'MyExistingController' is already joined.&lt;br&gt;The credentials contained within '\$credentialSite' will be used to add the necessary permissions for 'MyNewController' to the Site Configuration Database. The credentials contained within '\$credentialLogging' will be used to add the necessary permissions for 'MyNewController' to the Configuration Logging Database. The credentials contained within '\$credentialMonitor' will be used to add the necessary permissions for 'MyNewController' to the Monitoring Database.
