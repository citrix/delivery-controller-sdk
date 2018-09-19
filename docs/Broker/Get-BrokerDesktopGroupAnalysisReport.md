# Get-BrokerDesktopGroupAnalysisReport

   Gets the detailed AppDNA compatibility report for AppDisk(s) associated with a particular Desktop Group.

## Syntax
```
Get-BrokerDesktopGroupAnalysisReport [-InputObject] <DesktopGroup[]> [-RetrieveReportContentsAsMHT] [-AdminAddress <String>] [[-AppDiskUid] <Guid>] [<CommonParameters>]
```

## Detailed Description
   Gets the detailed AppDNA compatibility report for an AppDisk associated with a particular Desktop Group.

## Related Commands
  * [Get-BrokerDesktopGroup](Get-BrokerDesktopGroup/)
  * [Set-BrokerDesktopGroup](Set-BrokerDesktopGroup/)
  * [Get-AppLibAppDisk](Get-AppLibAppDisk/)
## Parameters

| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| InputObject | The desktop group(s) on which to retrieve the detailed reports | true | true (ByValue) |  |
| RetrieveReportContentsAsMHT | Retrieve the report as a MHT file | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |
| AppDiskUid | AppDisk unique identifier. If set, the report will be filtered down to only include this AppDisk. | false | false |  |

## Input Type
### Citrix.Broker.Admin.SDK.DesktopGroup
   You can pipe the desktop groups to Get-BrokerDesktopGroupAnalysisReport.
## Return Values
### Citrix.Broker.Admin.SDK.AnalysisReport
   The analysis reports for the desktop groups
## Examples

### EXAMPLE 1
```
Get-BrokerDesktopGroupAnalysisReport -InputObject 36
```
   Description<br>-----------<br>Retrieves the report for the desktop group with Uid 36
### EXAMPLE 2
```
$appDisk = Get-AppLibAppDisk -AppDiskName "MyAppDisk"
          Get-BrokerDesktopGroupAnalysisReport -InputObject 36 -AppDiskUid $appDisk.AppDiskUid
```
   Description<br>-----------<br>Retrieves the report for the desktop group with Uid 36 filtered down to AppDisk "MyAppDisk"
