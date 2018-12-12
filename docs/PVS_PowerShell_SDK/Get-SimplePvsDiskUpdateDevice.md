
# Get-Simplepvsdiskupdatedevice

## Syntax
```
Get-SimplePvsDiskUpdateDevice [-deviceId <string[]>] [-deviceName <string[]>] [-deviceMac <string[]>] [-siteId <string[]>] [-siteName <string[]>] [-diskLocatorId <string[]>] [-updateTaskId <string[]>] [-site <PvsSite[]>] [-diskLocator <PvsDiskLocator[]>] [-updateTask <PvsUpdateTask[]>] [-sortBy <string>] [<CommonParameters>]
```
## Detailed Description

## Related Commands

## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| deviceId |  | false | false |  |
| deviceMac |  | false | false |  |
| deviceName |  | false | false |  |
| diskLocator |  | false | true (ByValue) |  |
| diskLocatorId |  | false | false |  |
| site |  | false | true (ByValue) |  |
| siteId |  | false | false |  |
| siteName |  | false | false |  |
| sortBy |  | false | false |  |
| updateTask |  | false | true (ByValue) |  |
| updateTaskId |  | false | false |  |

## Input Type

### Citrix.Pvs.Powershell.Commands.Pvssite\[\]<br>Citrix.Pvs.Powershell.Commands.Pvsdisklocator\[\]<br>Citrix.Pvs.Powershell.Commands.Pvsupdatetask\[\]

## Return Values

### System.Object

