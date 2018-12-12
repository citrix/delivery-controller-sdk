
# Get-Citrixcallhomeschedule
Returns the frequency and time of day when scheduled Call Home uploads will occur.
## Syntax
```
Get-CitrixCallHomeSchedule [-InformationAction <ActionPreference>] [-InformationVariable <String>] [<CommonParameters>]
```
## Detailed Description
This cmdlet returns the settings for the recurring Call Home uploads.

The result is a custom object containing the fields:

UploadFrequency - The desired upload frequency. Either "Daily" or "Weekly"

DayOfWeek - The weekday on which the recurring Call Home upload will occur.  One of "Monday", "Tuesday", "Wednesday", "Thursday", "Friday", "Saturday", "Sunday". This is ignored when the UploadFrequency is set to "Daily".

StartTime - A System.TimeSpan representing the duration after midnight at which to start a two hour window during which a scheduled Call Home upload will occur.


## Related Commands

* [Disable-CitrixCallHome](./Disable-CitrixCallHome/)
* [Enable-CitrixCallHome](./Enable-CitrixCallHome/)
* [Get-CitrixCallHome](./Get-CitrixCallHome/)
* [Set-CitrixCallHomeSchedule](./Set-CitrixCallHomeSchedule/)
* [Start-TelemetryUpload](./Start-TelemetryUpload/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| InformationAction |  | false | false |  |
| InformationVariable |  | false | false |  |

## Input Type

### 

## Return Values

### Citrixcallhomeschedule
A custom object containing the fields:<br>UploadFrequency - The desired upload frequency. Either "Daily" or "Weekly"<br>DayOfWeek - The weekday on which the recurring Call Home upload will occur.  One of "Monday", "Tuesday", "Wednesday", "Thursday", "Friday", "Saturday", "Sunday". This is ignored when the UploadFrequency is set to "Daily".<br>StartTime - A System.TimeSpan representing the duration after midnight at which to start a two hour window during which a scheduled Call Home upload will occur.
## Examples

### Example 1: Get The Citrix Call Home Recurring Upload Settings
```
PS C:\>Get-CitrixCallHomeSchedule
```Returns the frequency (either Daily or Weekly) and time of day when scheduled Call Home uploads will occur.&lt;br&gt;Note that the actual upload will occur within a two hour window starting from the scheduled time of day.
