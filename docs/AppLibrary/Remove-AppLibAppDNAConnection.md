# Remove-AppLibAppDNAConnection

   Removes the AppDNA connection.

## Syntax
```
Remove-AppLibAppDNAConnection [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
```

## Detailed Description
   Removes the AppDNA connection configuration from Citrix Studio thereby disabling Studio's integration with AppDNA.

## Related Commands
  * [Get-AppLibAppDNAConnection](Get-AppLibAppDNAConnection.html)
  * [Set-AppLibAppDNAConnection](Set-AppLibAppDNAConnection.html)
  * [Enable-AppLibAppDNAConnection](Enable-AppLibAppDNAConnection.html)
  * [Disable-AppLibAppDNAConnection](Disable-AppLibAppDNAConnection.html)
## Parameters

| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| LoggingId | Specifies the identifier of the high-level operation this cmdlet call forms a part of. Citrix Studio and Director typically create high-level operations. PowerShell scripts can also wrap a series of cmdlet calls in a high-level operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller the PowerShell snap-in will connect to. You can provide this as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type
### 
   
## Return Values
### void
   ## Notes
   Removing the AppDNA connection will disable any integration Citrix Studio has with AppDNA data.
## Examples

### EXAMPLE 1
```
C:\PS>Remove-AppLibAppDNAConnection
```
   Description<br>-----------<br>Removes the AppDNA integration from Citrix Studio
