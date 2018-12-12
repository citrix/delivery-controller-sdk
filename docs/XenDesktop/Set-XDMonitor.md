
# Set-Xdmonitor
Sets the Monitoring Database attributes of a Site.
## Syntax
```
Set-XDMonitor [-DatabaseMirrorServer <String>] [-DatabaseName <String>] [-DatabaseServer <String>] [-PassThru] [-AdminAddress <String>] [<CommonParameters>]
```
## Detailed Description
Sets the Monitoring Database attributes of the Site which has a Controller identified by AdminAddress.


## Related Commands

* [Get-XDMonitor](./Get-XDMonitor/)
* [Get-XDSite](./Get-XDSite/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| DatabaseMirrorServer | The mirror database server for the Monitoring Database. If this parameter is not provided, the mirror server is determined by querying the SQL Server hosting the Monitoring Database. | false | false |  |
| DatabaseName | The name of the Monitoring Database. If this is omitted, the name is assumed to be the existing Monitoring Database name. | false | false |  |
| DatabaseServer | The database server for the Monitoring Database. If not provided, the server is assumed to be the SQL Server that is hosting the existing Monitoring Database. | false | false |  |
| PassThru | Returns the affected record. By default, this cmdlet does not generate any output. | false | false | False |
| AdminAddress | Specifies the address of the Delivery Controller to which the PowerShell module will connect. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |

## Input Type

### None
You cannot pipe input to this cmdlet.
## Return Values

### None Or Citrix.Xendesktoppowershellsdk.Serviceinterfaces.Configuration.Monitor
This cmdlet does not generate any output, unless you use the PassThru parameter, in which case it generates a Citrix.XenDesktopPowerShellSdk.ServiceInterfaces.Configuration.Monitor object.
## Notes
The command can fail for the following reasons:<br>    o The Monitoring Database name and/or database server have not been provided, yet there is no existing database name and/or database server to use as default settings.<br>    o The Controller identfied by AdminAddress does not have the necessary permissions to access the new Monitoring Database or mirror database on the database server.<br>    o The new Monitoring Database or mirror database on the database server is not configured for the Site that is associated with the Controller identified by AdminAddress.
## Examples

### Example 1
```
C:\PS> Set-XDMonitor -AdminAddress MyController -DatabaseMirrorServer MySQLMirror
```
#### Description
For the Site managed by MyController, sets the mirror for the Monitoring Database to MySQLMirror.
### Example 2
```
C:\PS> Set-XDMonitor -AdminAddress MyController -DatabaseServer MySQLServer -DatabaseName MyMonitorDatabase
```
#### Description
For the Site managed by MyController, sets the SQL Server for the Monitoring Database to MySQLServer and the database name to MyMonitorDatabase.
