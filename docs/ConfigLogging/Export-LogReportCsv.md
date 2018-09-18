# Export-LogReportCsv

   Exports Configuration Logging data into a CSV file.

## Syntax
```
Export-LogReportCsv -OutputFile <String> [-StartDateRange <DateTime>] [-EndDateRange <DateTime>] [-AdminAddress <String>] [<CommonParameters>]
```

## Detailed Description
   This cmdlet exports the Configuration Logging data into a CSV data file. The hierarchical logging data is flattened into a single CSV ‘table’. The content of CSV file is not intended to be human-readable. It is meant to be input data for external reporting or manipulation tools (for example, a spread sheet application).

## Related Commands
  * [Export-LogReportHtml](Export-LogReportHtml/)
## Parameters

| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| OutputFile | Specifies the path to a file where the CSV data will be saved. | true | false |  |
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
C:\PS> Export-LogReportCsv -OutputFile "c:\MyReports\LoggingData.csv"
```
   Description<br>-----------<br>Export all logged operations to a csv file.
### EXAMPLE 2
```
C:\PS> Export-LogReportCsv -OutputFile "c:\MyReports\LoggingData.csv" -StartDateRange "2012-12-21 09:00"
```
   Description<br>-----------<br>Export to a CSV file logged operations started on or after a specified datetime..
### EXAMPLE 3
```
C:\PS> Export-LogReportCsv -OutputFile "c:\MyReports\LoggingData.csv" -StartDateRange "2012-12-21 09:00" -EndDateRange "2012-12-311 18:00"
```
   Description<br>-----------<br>Export to a CSV file logged operations started and completed between a date range.
