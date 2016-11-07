# Set-EnvTestConfiguration

   Sets the Environment Test Service's configuation options

## Syntax
```
Set-EnvTestConfiguration [-PerTypeDiscoveredObjectLimit <Int32>] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
```

## Detailed Description
   Sets the Environment Test Service's configuation options and broadcasts the changes to other machines in the Site.

## Related Commands
## Parameters

| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| PerTypeDiscoveredObjectLimit | Sets the maximum number of objects of a particular type to be explored when discovering objects during a test run.  Default: 50 | false | false |  |
| LoggingId | Specifies the identifier of the high-level operation this cmdlet call forms a part of. Citrix Studio and Director typically create high-level operations. PowerShell scripts can also wrap a series of cmdlet calls in a high-level operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller the PowerShell snap-in will connect to. You can provide this as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type
### Integer
   Must be greater than zero.
## Return Values
### System.String
   
## Examples

### EXAMPLE 1
```
Set-EnvTestConfiguration -PerTypeDiscoveredObjectLimit 100
```
   Description<br>-----------<br>Set the maximum to 100
