# Get-AppLibAppDNAConnection

   Gets the AppDNA connection details.

## Syntax
```
Get-AppLibAppDNAConnection [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
```

## Detailed Description
   Gets the AppDNA Connection details used to integrate Citrix Studio with AppDNA.

## Related Commands
  * [Set-AppLibAppDNAConnection](Set-AppLibAppDNAConnection/)
  * [Remove-AppLibAppDNAConnection](Remove-AppLibAppDNAConnection/)
  * [Enable-AppLibAppDNAConnection](Enable-AppLibAppDNAConnection/)
  * [Disable-AppLibAppDNAConnection](Disable-AppLibAppDNAConnection/)
## Parameters

| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| LoggingId | Specifies the identifier of the high-level operation this cmdlet call forms a part of. Citrix Studio and Director typically create high-level operations. PowerShell scripts can also wrap a series of cmdlet calls in a high-level operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller the PowerShell snap-in will connect to. You can provide this as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type
### 
   
## Return Values
### Citrix.AppLibrary.Sdk.AppDNAConnection<br>                    This object provides details of the AppDNA Connection and contains the following information:<br>                    Address <string><br>                    The URL of the AppDNA web server.<br>                    Database <string><br>                    The database identifier from the AppDNA site<br>                    Enabled <bool><br>                    Whether or not the connection is enabled<br>                    Username <string><br>                    The user account name used to make the connection.
   ## Notes
   The AppDNA user's password is never returned with the connection details.
## Examples

### EXAMPLE 1
```
C:\PS>Get-AppLibAppDNAConnection

                    Address  : http://AppDNAServer.mynetwork.net:8199/AppDNA
                    Database : AppDNAServer:AppDNADB
                    Enabled  : True
                    UserName : AppDNAUser
```
   Description<br>-----------<br>Gets the AppDNA Connection details used to integrate Citrix Studio with AppDNA.
