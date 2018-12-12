
# Remove-Xdcontroller
Removes a Delivery Controller from an existing Site
## Syntax
```
Remove-XDController -DatabaseCredentials <PSCredential> -ControllerName <String> [-AdminAddress <String>] [<CommonParameters>]

Remove-XDController -ControllerName <String> [-DoNotUpdateDatabaseServer] [-AdminAddress <String>] [<CommonParameters>]

Remove-XDController -LoggingDatabaseCredentials <PSCredential> -MonitorDatabaseCredentials <PSCredential> -SiteDatabaseCredentials <PSCredential> -ControllerName <String> [-AdminAddress <String>] [<CommonParameters>]
```
## Detailed Description
Removes a Controller from an existing Site that currently has more than one Controller.

If no credentials are provided and DoNotUpdateDatabaseServer has not been specified, then all database update operations are attempted using the credentials of the user running the cmdlet.

If DatabaseCredentials is provided, then all database operations are attempted using the credentials.

If one or more of SiteDatabaseCredentials, LoggingDatabaseCredentials or MonitorDatabaseCredentials are provided, then all three must be provided. All operations are then attempted using the credentials appropriate to each Database.


## Related Commands

* [Add-XDController](./Add-XDController/)
* [Get-XDDatabaseSchema](./Get-XDDatabaseSchema/)
* [Get-XDSite](./Get-XDSite/)
* [Remove-XDSite](./Remove-XDSite/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| ControllerName | The name of the Controller that is to be removed. This may be in SID, DNS or SAM name form.  This cannot be the same as the Controller identified by AdminAddress. | true | false |  |
| DatabaseCredentials | The security credentials, in the form of a PSCredential object, that will be used to connect to the SQL Servers associated with the Site Configuration, Configuration Logging and Monitoring Databases. | true | false |  |
| LoggingDatabaseCredentials | The security credentials, in the form of a PSCredential object, that will be used to connect to the SQL Server associated with the Configuration Logging Database. | true | false |  |
| MonitorDatabaseCredentials | The security credentials, in the form of a PSCredential object, that will be used to connect to the SQL Server associated with the Monitoring Database. | true | false |  |
| SiteDatabaseCredentials | The security credentials, in the form of a PSCredential object, that will be used to connect to the SQL Server associated with the Site Configuration Database. | true | false |  |
| AdminAddress | Specifies the address of the Delivery Controller to which the PowerShell module will connect. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |
| DoNotUpdateDatabaseServer | Results in the permissions associated with the Controller not being automatically removed from the Database.<br>This switch may be useful when the person running the cmdlet has insufficient database privilege.  The database permissions for the Controller must be removed manually after running this cmdlet.<br>Get-XDDatabaseSchema may be used to generate the SQL script which in turn may be used to remove the associated permissions from the Database.<br>This parameter results in all supplied credentials being ignored. | false | false |  |

## Input Type

### None
You cannot pipe input to this cmdlet.
## Return Values

### None

## Notes
If the user running this cmdlet does not have privilege to remove users from the Database, then either use the DoNotudpateDatabaseServer switch or supply alternative credentials using one or more of the Credentials arguments.<br>    This cmdlet cannot be used to remove the last Controller from a Site; use the Remove-XDSite cmdlet instead.<br>    The command can fail for the following reasons:<br>    o The Site has only one Controller. A Site must have multiple Controllers before a Controller can be removed.<br>    o The Controller that is to be removed is not a member of the Site.<br>    o The person running the cmdlet, or the supplied credentials, does not have sufficient privilege to update the Database. Either run this cmdlet as a user that has administrator privilege to the Database, or supply an account with suitable privileges using the PSCredential parameter(s).
## Examples

### Example 1
```
C:\PS> Remove-XDController -AdminAddress MyExistingController -ControllerName MyControllerToRemove
```
#### Description
Removes the Controller 'MyControllerToRemove' from the Site to which 'MyExistingController' is joined.  The permissions associated with 'MyControllerToRemove' will be automatically removed from the Database using the implicit credentials of the user running the cmdlet.
### Example 2
```
C:\PS> Remove-XDController -AdminAddress MyExistingController -ControllerName MyControllerToRemove -DoNotUpdateDatabaseServer

C:\PS> Get-XDDatabaseSchema -AdminAddress MyExistingController -SiteName MySite -DatabaseServer MySQLServer -ScriptType RemoveController -ControllerToRemoveSid MyControllerToRemove_SID > C:\removeController.sql

C:\PS> # Although not necessary, Citrix recommends you get a database administrator to run removeController.sql
```
#### Description
Removes the Controller 'MyControllerToRemove' from the Site to which 'MyExistingController' is joined.&lt;br&gt;The permissions for 'MyNewController' will not be removed from the Database.  Instead the Get-XDDatabaseSchema cmdlet is used to generate a SQL script that may be given to the database administrator of 'MySQLServer'.  The SQL script may be used to remove the permissions that previously allowed 'MyControllerToRemove' to manipulate data within the Database.
### Example 3
```
C:\PS> $credential = Get-Credential

C:\PS> Remove-XDController -AdminAddress MyExistingController -ControllerName MyControllerToRemove -DatabaseCredentials $credential
```
#### Description
Removes the Controller 'MyControllerToRemove' from the Site to which 'MyExistingController' is joined.&lt;br&gt;The credentials contained within '\$credential' will be used to remove the permissions associated with 'MyControllerToRemove' from the Database.
### Example 4
```
C:\PS> $credentialSite = Get-Credential

C:\PS> $credentialLogging = Get-Credential

C:\PS> $credentialMonitor = Get-Credential

C:\PS> Remove-XDController -AdminAddress MyExistingController -ControllerName MyControllerToRemove -SiteDatabaseCredentials $credentialSite -LoggingDatabaseCredentials $credentialLogging -MonitorDatabaseCredentials $credentialMonitor
```
#### Description
Removes the Controller 'MyControllerToRemove' from the Site to which 'MyExistingController' is joined.&lt;br&gt;The credentials contained within '\$credentialSite' will be used to remove the permissions associated with 'MyControllerToRemove' from the Site Configuration Database. The credentials contained within '\$credentialLogging' will be used to remove the permissions associated with 'MyControllerToRemove' from the Configuration Logging Database. The credentials contained within '\$credentialMonitor' will be used to remove the permissions associated with 'MyControllerToRemove' from the Monitoring Database.
