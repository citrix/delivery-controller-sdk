
# Set-Xdlogging
Sets the Configuration Logging Database attributes of a Site.
## Syntax
```
Set-XDLogging [-DatabaseMirrorServer <String>] [-DatabaseName <String>] [-DatabaseServer <String>] [-Enabled <Boolean>] [-Locale <String>] [-PassThru] [-AdminAddress <String>] [<CommonParameters>]
```
## Detailed Description
Sets the Configuration Logging Database attributes of the Site which has a Controller identified by AdminAddress.


## Related Commands

* [Get-XDLogging](./Get-XDLogging/)
* [Get-XDSite](./Get-XDSite/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| DatabaseMirrorServer | The mirror database server for the Configuration Logging Database. If this parameter is not provided, the mirror server is determined by querying the SQL Server hosting the Configuration Logging Database. | false | false |  |
| DatabaseName | The name of the Configuration Logging Database. If this is omitted, the name is assumed to be the existing Configuration Logging Database name. | false | false |  |
| DatabaseServer | The database server for the Configuration Logging Database. If not provided, the server is assumed to be the SQL Server that is hosting the existing Configuration Logging Database. | false | false |  |
| Enabled | Determines if Configuration Logging is enabled. | false | false |  |
| Locale | The language used for Configuration Logging entries. Supported locales are English, Japanese and Chinese. | false | false |  |
| PassThru | Returns the affected record. By default, this cmdlet does not generate any output. | false | false | False |
| AdminAddress | Specifies the address of the Delivery Controller to which the PowerShell module will connect. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |

## Input Type

### None
You cannot pipe input to this cmdlet.
## Return Values

### None Or Citrix.Xendesktoppowershellsdk.Serviceinterfaces.Configuration.Logging
This cmdlet does not generate any output, unless you use the PassThru parameter, in which case it generates a Citrix.XenDesktopPowerShellSdk.ServiceInterfaces.Configuration.Logging object.
## Notes
When Configuration Logging is enabled, the dynamic parameter "AllowDisconnectedDatabase" may be used to permit Configuration operations to proceed even if the Configuration Logging Database is not available.<br>    The command can fail for the following reasons:<br>    o The Configuration Logging Database name and/or database server have not been provided, yet there is no existing database name and/or database server to use as default settings.<br>    o The Controller identfied by AdminAddress does not have the necessary permissions to access the new Configuration Loggging Database or mirror database on the database server.<br>    o The new Configuration Loggging Database or mirror database on the database server is not configured for the Site that is associated with the Controller identified by AdminAddress.
## Examples

### Example 1
```
C:\PS> Set-XDLogging -AdminAddress MyController -Enabled $true
```
#### Description
For the Site managed by MyController, enables Configuration Logging.
### Example 2
```
C:\PS> Set-XDLogging -AdminAddress MyController -Enabled $true -AllowDisconnectedDatabase $true
```
#### Description
For the Site managed by MyController, enables Configuration Logging and allows configuration operations to succeed even if the Configuration Logging Database is unavailable. Note that Configuration Logging must be enabled before AllowDisconnectedDatabase can be set to \$true.
### Example 3
```
C:\PS> Set-XDLogging -AdminAddress MyController -DatabaseMirrorServer MySQLMirror
```
#### Description
For the Site managed by MyController, sets the mirror for the Configuration Logging Database to MySQLMirror.
### Example 4
```
C:\PS> Set-XDLogging -AdminAddress MyController -DatabaseServer MySQLServer -DatabaseName MyConfigLoggingDatabase
```
#### Description
For the Site managed by MyController, sets the SQL Server for the Configuration Logging Database to MySQLServer and the database name to MyConfigLoggingDatabase.
