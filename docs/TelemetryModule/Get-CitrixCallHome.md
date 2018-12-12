
# Get-Citrixcallhome
Returns the current configuration of Call Home.
## Syntax
```
Get-CitrixCallHome [-InformationAction <ActionPreference>] [-InformationVariable <String>] [<CommonParameters>]
```
## Detailed Description
This cmdlet returns the current configuration of Call Home in a custom object containing the fields:

IsEnabled - A boolean value indicating if Call Home is currently enabled.

IsMasterImage - A boolean value indicating if the current configuration is prepared for further replication.


## Related Commands

* [Disable-CitrixCallHome](./Disable-CitrixCallHome/)
* [Enable-CitrixCallHome](./Enable-CitrixCallHome/)
* [Set-CitrixCallHomeSchedule](./Set-CitrixCallHomeSchedule/)
* [Get-CitrixCallHomeSchedule](./Get-CitrixCallHomeSchedule/)
* [Start-TelemetryUpload](./Start-TelemetryUpload/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| InformationAction |  | false | false |  |
| InformationVariable |  | false | false |  |

## Input Type

### 

## Return Values

### Citrixcallhome
A custom object containing the fields:<br>IsEnabled - A boolean value indicating if Call Home is currently enabled.<br>IsMasterImage - A boolean value indicating if the current configuration is prepared for further replication.
## Examples

### Example 1: Get The Citrix Call Home Configuration
```
C:\PS>Get-CitrixCallHome
```Determine if Citrix Call Home is enabled and if it is configured as a Master Image
