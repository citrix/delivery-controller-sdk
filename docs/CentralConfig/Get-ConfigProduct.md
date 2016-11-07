# Get-ConfigProduct

   Lists the site's supported product names and codes.

## Syntax
```
Get-ConfigProduct [-AdminAddress <String>] [<CommonParameters>]
```

## Detailed Description
   

## Related Commands
  * [Get-ConfigSite](Get-ConfigSite.html)
  * [Set-ConfigSite](Set-ConfigSite.html)
## Parameters

| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| AdminAddress | Specifies the address of a XenDesktop controller the PowerShell snap-in will connect to. You can provide this as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type
### 
   
## Return Values
### PSObject
   
## Examples

### EXAMPLE 1
```
C:\PS> Get-ConfigProduct
```
   Description<br>-----------<br>Lists the supported products by name and code.
