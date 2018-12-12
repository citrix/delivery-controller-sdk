
# Disable-Citrixcallhome
Disables the scheduled Call Home uploads and removes the Citrix identity from the machine.
## Syntax
```
Disable-CitrixCallHome [-InformationAction <ActionPreference>] [-InformationVariable <String>] [<CommonParameters>]
```
## Detailed Description
This cmdlet disables the scheduled Call Home uploads and removes the Citrix identity from the machine.


## Related Commands

* [Enable-CitrixCallHome](./Enable-CitrixCallHome/)
* [Get-CitrixCallHome](./Get-CitrixCallHome/)
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

### 

## Examples

### Example 1: Disabling Call Home
```
PS C:\>Disable-CitrixCallHome
```Disables automatic upload and removes Citrix identity from the machine.
