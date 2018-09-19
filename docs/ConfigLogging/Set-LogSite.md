# Set-LogSite

   Sets global configuration logging settings.

## Syntax
```
Set-LogSite [-State <LoggingState>] [-Locale <String>] [-PassThru] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
```

## Detailed Description
   This cmdlet sets the global configuration logging settings.

## Related Commands
  * [Get-LogSite](Get-LogSite/)
## Parameters

| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| State | Sets the state of configuration logging. Values can be:<br>o Enabled - state changes will be logged. If logging is unavailable, the state change will still be permitted. o Disabled - state changes will not be logged.<br>o Mandatory - state change will be logged. If logging is unavailable, the state change will not be permitted.<br>When the state is set to Enabled or Mandatory, XenDesktop services will attempt to log operations (which perform configuration changes) before performing them. | false | false |  |
| Locale | Sets the language that logs should be recorded in. Values can be: 'en', 'ja', 'zh-CN', 'de', 'es' or 'fr'. | false | false |  |
| PassThru | Returns the affected record. By default, this cmdlet does not generate any output. | false | false | False |
| LoggingId | Specifies the identifier of the high-level operation this cmdlet call forms a part of. Citrix Studio and Director typically create high-level operations. PowerShell scripts can also wrap a series of cmdlet calls in a high-level operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller the PowerShell snap-in will connect to. You can provide this as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type
### 
   
## Return Values
### Citrix.ConfigurationLogging.Sdk.Site
   Current logging settings## Notes
   Configuration logging will automatically transition to a 'NotSupported' state if the logging feature is not licensed. Set-LogSite will reject request to set logging to 'Enabled' or 'Mandatory' while the logging feature is not licensed.
## Examples

### EXAMPLE 1
```
C:\PS> Set-LogSite -Locale "zh-CN"
```
   Description<br>-----------<br>Set the logging language to Chinese. The logging state will be unchanged.
### EXAMPLE 2
```
C:\PS> Set-LogSite -State "Mandatory"
```
   Description<br>-----------<br>Set the logging state to mandatory. The logging locale will be unaffected. In this state, no configuration change will be allowed unless it is successfully logged.
### EXAMPLE 3
```
C:\PS> Set-LogSite -Locale "de" -State "Enabled"
```
   Description<br>-----------<br>Set the logging language to German and the state to Enabled.
