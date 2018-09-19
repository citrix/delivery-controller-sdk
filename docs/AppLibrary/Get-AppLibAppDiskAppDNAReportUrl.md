# Get-AppLibAppDiskAppDNAReportUrl

   Gets the AppDNA compatibility report an AppDisk.

## Syntax
```
Get-AppLibAppDiskAppDNAReportUrl [-AppDiskUid] <Guid> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
```

## Detailed Description
   Gets the detailed AppDNA compatibility report for the specified AppDisk.

## Related Commands
  * [Get-AppLibDesktopGroupAppDNAReport](Get-AppLibDesktopGroupAppDNAReport/)
  * [Get-AppLibDesktopGroupAppDiskAppDNAReport](Get-AppLibDesktopGroupAppDiskAppDNAReport/)
  * [Get-AppLibAppDisk](Get-AppLibAppDisk/)
## Parameters

| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| AppDiskUid | The unique identifier of the AppDisk for which to retrieve the report. | true | false |  |
| LoggingId | Specifies the identifier of the high-level operation this cmdlet call forms a part of. Citrix Studio and Director typically create high-level operations. PowerShell scripts can also wrap a series of cmdlet calls in a high-level operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller the PowerShell snap-in will connect to. You can provide this as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type
### String
   
## Return Values
### Citrix.AppLibrary.Sdk.AppLibraryStatus
   An object indicating the success of the report export operation
## Examples

### EXAMPLE 1
```
C:\PS>Get-AppLibAppDiskAppDNAReport -AppDiskUid "F0A272E2-0268-48E3-8855-CFED44236B8E" -FileName "C:\Windows\Temp\Report.mht"
```
   Description<br>-----------<br>Saves the report of the specified AppDisk to C:\Windows\Temp\Report.mht
### EXAMPLE 2
```
C:\PS>$AppDisk = Get-AppLibAppDisk -Name "MyAppDisk"
            C:\PS>Get-AppLibAppDiskAppDNAReport -AppDiskUid $AppDisk.ApppDiskUid -FileName "C:\Windows\Temp\Report.mht"
            C:\PS>Invoke-Item "C:\Windows\Temp\Report.mht"
```
   Description<br>-----------<br>Finds the Uid for the AppDisk named "My AppDisk" and uses it to save the report to C:\Windows\Temp\Report.mht
