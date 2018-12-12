# Get-ConfigSite

   Gets the site.

## Syntax
```
Get-ConfigSite [-BearerToken <String>] [-AdminAddress <String>] [<CommonParameters>]
```

## Detailed Description
   The Get-ConfigSite cmdlet gets the site.

A XenDesktop installation has only a single site instance.

## Related Commands
  * [Set-ConfigSite](Set-ConfigSite.html)
  * [Import-ConfigFeatureTable](Import-ConfigFeatureTable.html)
## Parameters

| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
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
