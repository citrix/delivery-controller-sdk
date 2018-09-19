# Get-ConfigSite

   Gets the site.

## Syntax
```
Get-ConfigSite [-AdminAddress <String>] [<CommonParameters>]
```

## Detailed Description
   The Get-ConfigSite cmdlet gets the site.

A XenDesktop installation has only a single site instance.

## Related Commands
  * [Set-ConfigSite](Set-ConfigSite/)
  * [Import-ConfigFeatureTable](Import-ConfigFeatureTable/)
## Parameters

| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| AdminAddress | Specifies the address of a XenDesktop controller the PowerShell snap-in will connect to. You can provide this as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type
### 
   
## Return Values
### Get-ConfigSite returns the site instance.
   
## Examples

### EXAMPLE 1
```
C:\PS> Get-ConfigSite
```
   Description<br>-----------<br>Gets the site.
