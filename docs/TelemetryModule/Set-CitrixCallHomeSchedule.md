
# Set-Citrixcallhomeschedule
Sets the frequency and time of day at which scheduled Call Home uploads will occur.
## Syntax
```
Set-CitrixCallHomeSchedule [-TimeOfDay <[TimeSpan]>] [-UploadFrequency <[UploadFrequency]>] [-DayOfWeek <[DayOfWeek]>] [-AppendHeaders <String>] [-InformationAction <ActionPreference>] [-InformationVariable <String>] [<CommonParameters>]
```
## Detailed Description
This cmdlet allows the administrator to set the recurrence details for automatic Citrix Call Home uploads. When you Enable-CitrixCallHome, the upload recurrence defaults to once per week, at 3:00 AM local time on Sunday morning.

Note that time of day is the start of a two hour window. The uploads are randomly distributed over this window to balance network resource consumption.


## Related Commands

* [Get-Credential](./Get-Credential/)
* [New-TimeSpan](./New-TimeSpan/)
* [Disable-CitrixCallHome](./Disable-CitrixCallHome/)
* [Enable-CitrixCallHome](./Enable-CitrixCallHome/)
* [Get-CitrixCallHome](./Get-CitrixCallHome/)
* [Get-CitrixCallHomeSchedule](./Get-CitrixCallHomeSchedule/)
* [Start-TelemetryUpload](./Start-TelemetryUpload/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| TimeOfDay | System.TimeSpan representing the duration after midnight at which to start a two hour window during which a scheduled Call Home upload will occur. | false | false | 3:00 AM |
| UploadFrequency | The desired upload frequency. Either "Daily" or "Weekly" | false | false | Weekly |
| DayOfWeek | The weekday on which the recurring Call Home upload will occur.  One of "Monday", "Tuesday", "Wednesday", "Thursday", "Friday", "Saturday", "Sunday". This is ignored when the UploadFrequency is set to "Daily". | false | false | Sunday |
| AppendHeaders | Specify the appended headers uploaded to CIS. Json-formatted. | false | true (ByPropertyName) |  |
| InformationAction |  | false | false |  |
| InformationVariable |  | false | false |  |
| Streaming | Specify the parameter boolean parameter to enable/disable Streaming of upload bundles. Streaming is enabled by default. | false | true (ByPropertyName) |  |
| ParallelCollection | Specify the parameter boolean parameter to enable/disable Parallel Colelction of upload bundles. Parallel Collection is enabled by default. | false | true (ByPropertyName) |  |

## Input Type

### 

## Return Values

### 

## Examples

### Example 1: Set The Upload Time To 4:15 Am
```
PS C:\>$newTime = New-TimeSpan -Hours 4 –Minutes 15

PS C:\>Set-CitrixCallHomeSchedule -TimeOfDay $newTime
```Sets the upload window to begin at 4:15 AM.
### Example 2: Set The Uploads To 11:30 Pm On Friday
```
PS C:\>$newTime = New-TimeSpan -Hours 23 –Minutes 30

PS C:\>Set-CitrixCallHomeSchedule -TimeOfDay $newTime -DayOfWeek Friday -UploadFrequency Weekly
```Sets the uploads to occur Fridays in a window beginning at 11:30 PM.
### Example 3: Set The Uploads Occur Daily At 2 Am
```
PS C:\>$newTime = New-TimeSpan -Hours 2

PS C:\>Set-CitrixCallHomeSchedule -TimeOfDay $newTime -UploadFrequency Daily
```Sets the uploads to occur daily in a window beginning at 2:00 AM.
### Example 4: Set The Uploads Occur Daily At 2 Am With Appended Headers
```
PS C:\>$newTime = New-TimeSpan -Hours 2

PS C:\>Set-CitrixCallHomeSchedule -TimeOfDay $newTime -UploadFrequency Daily -AppendHeaders "{'key1':'value1'}"
```Sets the uploads to occur daily in a window beginning at 2:00 AM with appended headers.
