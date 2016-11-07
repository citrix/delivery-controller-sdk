# Export-LogReportHtml

   Exports Configuration Logging data into a HTML report.

## Syntax
```
Export-LogReportHtml -OutputDirectory <String> [-StartDateRange <DateTime>] [-EndDateRange <DateTime>] [-AdminAddress <String>] [<CommonParameters>]
```

## Detailed Description
   This cmdlet exports the Configuration Logging data into a HTML report. The report consists of two HTML files:
o Summary.Html - this shows summary information from the high level operation logs.
o Details.Html - this shows additional logging data from the low level operation and operation detail logs.
Hyperlinks in summary.html allow drill-down into the associated low level logging data contained within details.html.

## Related Commands
  * [Export-LogReportCsv](Export-LogReportCsv.html)
## Parameters

| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| OutputDirectory | Specifies the path to a directory where the HTML report files will will be saved. | true | false |  |
| StartDateRange | Specifies the start time of the earliest operation to include. | false | false | DateTime.Min |
| EndDateRange | Specifies the end time of the latest operation to include. | false | false | DateTime.UtcNow |
| AdminAddress | Specifies the address of a XenDesktop controller the PowerShell snap-in will connect to. You can provide this as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type
### 
   
## Return Values
### 
   
## Examples

### EXAMPLE 1
```
C:\PS> Export-LogReportHtml -OutputDirectory "c:\MyReports"
```
   Description<br>-----------<br>Export all logged operations to HTML.
### EXAMPLE 2
```
C:\PS> Export-LogReportHtml -OutputDirectory "c:\MyReports" -StartDateRange "2012-12-21 09:00"
```
   Description<br>-----------<br>Export to a HTML logged operations started on or after a specified datetime..
### EXAMPLE 3
```
C:\PS> Export-LogReportHtml -OutputDirectory "c:\MyReports" -StartDateRange "2012-12-21 09:00" -EndDateRange "2012-12-311 18:00"
```
   Description<br>-----------<br>Export to HTML logged operations started and completed between a date range.
