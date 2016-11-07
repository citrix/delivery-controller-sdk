# Set-AnalyticsSite

   This sets the site configuration for the Analytics Service/Customer Experience Improvement Program. Details are available at http://more.citrix.com/XD-CEIP

## Syntax
```
Set-AnalyticsSite [-Enabled <Boolean>] [-NewSite <Site>] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
```

## Detailed Description
   Use this cmdlet to opt-in to the Citrix Experience Improvement Program. For advanced users it can also take a new Citrix.Analytics.Sdk.Site object using the -NewSite parameter.

## Related Commands
## Parameters

| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| Enabled | This enables or disables the Citrix Experience Improvement Program functionality. | false | false | True |
| NewSite | New site object, if you wish to supply the a whole Site object. | false | false |  |
| LoggingId | Specifies the identifier of the high-level operation this cmdlet call forms a part of. Citrix Studio and Director typically create high-level operations. PowerShell scripts can also wrap a series of cmdlet calls in a high-level operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller the PowerShell snap-in will connect to. You can provide this as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type
### 
   
## Return Values
### 
   
## Examples

### EXAMPLE 1
```
c:\PS>Set-AnalyticsSite -Enabled $true
```
   Description<br>-----------<br>This enables the Citrix Experience Improvement Program. To disable use $false instead.
