# Set-AppLibAppDNAConnection

   Sets the connection details for integration of AppDNA into AppLibrary to allow AppDNA Analysis by this site.

## Syntax
```
Set-AppLibAppDNAConnection [-Address] <String> -Database <String> -UserName <String> -Password <SecureString> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
```

## Detailed Description
   Sets the connection details for integration of AppDNA into AppLibrary to allow AppDNA Analysis of AppDisk, Machines and DesktopGroups.

## Related Commands
  * [Get-AppLibAppDNAConnection](Get-AppLibAppDNAConnection.html)
  * [Remove-AppLibAppDNAConnection](Remove-AppLibAppDNAConnection.html)
  * [Enable-AppLibAppDNAConnection](Enable-AppLibAppDNAConnection.html)
  * [Deisable-AppLibAppDNAConnection](Deisable-AppLibAppDNAConnection.html)
## Parameters

| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| Address | The URL to the AppDNA web server. | true | false |  |
| Database | The AppDNA database identifier. | true | false |  |
| UserName | The username of the AppDNA user to connect with. | true | false |  |
| Password | The AppDNA user's password | true | false |  |
| LoggingId | Specifies the identifier of the high-level operation this cmdlet call forms a part of. Citrix Studio and Director typically create high-level operations. PowerShell scripts can also wrap a series of cmdlet calls in a high-level operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller the PowerShell snap-in will connect to. You can provide this as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type
### string
   ### System.Security.SecureString
   The secure string representing the user's password.
## Return Values
### Citrix.AppLibrary.Sdk.AppDNAConnection<br>                    This object provides details of the AppDNA Connection and contains the following information:<br>                    Address <string><br>                    The URL of the AppDNA web server.<br>                    Database <string><br>                    The database identifier from the AppDNA site<br>                    Enabled <bool><br>                    Whether or not the connection is enabled<br>                    Username <string><br>                    The user account name used to make the connection.
   ## Notes
   The AppDNA user's password is stored securely and is never returned in the AppDNAConnection object.<br>    Only one AppDNA configuration can be stored. If a connection is already set up, the connection details will be replaced.<br>    The connection will be enabled by default in the AppLibrary when the details are set.
## Examples

### EXAMPLE 1
```
C:\PS>$SecurePassword = ConvertTo-SecureString -String "password" -AsPlainText -Force
                    C:\PS>Set-AppLibAppDNAConnection -Address "http://my.appdna.server:8199/AppDNA" -Database "localhost:AppDNADB" -userName "AppDNAUser" -password $SecurePassword

                    Address  : http://my.appdna.server:8199/AppDNA
                    Database : localhost:AppDNADB
                    Enabled  : True
                    UserName : AppDNAUser
```
   Description<br>-----------<br>Sets the AppLibrary AppDNA connection to the configuration localhost:AppDNADB on my.appdna.server under the "AppDNAUser" account.
