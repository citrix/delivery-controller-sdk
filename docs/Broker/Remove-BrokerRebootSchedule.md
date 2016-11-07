# Remove-BrokerRebootSchedule

   Removes the reboot schedule.

## Syntax
```
Remove-BrokerRebootSchedule [-InputObject] <RebootSchedule[]> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]

Remove-BrokerRebootSchedule [-DesktopGroupName] <String> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
```

## Detailed Description
   The Remove-BrokerRebootSchedule cmdlet is used to delete an existing reboot schedule.

## Related Commands
  * [Get-BrokerRebootSchedule](Get-BrokerRebootSchedule.html)
  * [Set-BrokerRebootSchedule](Set-BrokerRebootSchedule.html)
  * [New-BrokerRebootSchedule](New-BrokerRebootSchedule.html)
  * [Stop-BrokerRebootCycle](Stop-BrokerRebootCycle.html)
## Parameters

| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| InputObject | The reboot schedule to be deleted. | true | true (ByValue) |  |
| DesktopGroupName | The name of the desktop group whose reboot schedule is to be removed. | true | true (ByPropertyName) |  |
| LoggingId | Specifies the identifier of the high level operation that this cmdlet call forms a part of. Desktop Studio and Desktop Director typically create High Level Operations. PowerShell scripts can also wrap a series of cmdlet calls in a High Level Operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |

## Input Type
### Citrix.Broker.Admin.SDK.RebootSchedule
   Reboot schedules may be specified through pipeline input.
## Return Values
### None
   
## Examples

### EXAMPLE 1
```
C:\PS> Get-BrokerRebootSchedule | Remove-BrokerRebootSchedule
```
   Description<br>-----------<br>Deletes every reboot schedule.
### EXAMPLE 2
```
C:\PS> Remove-BrokerRebootSchedule 12
```
   Description<br>-----------<br>Deletes the reboot schedule for the desktop group having Uid 12.
### EXAMPLE 3
```
C:\PS> Remove-BrokerRebootSchedule -DesktopGroupName Accounting
```
   Description<br>-----------<br>Deletes the reboot schedule for the desktop group named Accounting.
