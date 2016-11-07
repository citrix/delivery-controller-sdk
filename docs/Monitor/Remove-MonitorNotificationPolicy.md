# Remove-MonitorNotificationPolicy

   Removes persisted policy from the database by marking them as deleted

## Syntax
```
Remove-MonitorNotificationPolicy [-InputObject <MonitorNotificationPolicy[]>] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]

Remove-MonitorNotificationPolicy [-Uid <Int64[]>] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
```

## Detailed Description
   Removes the policy object from database by marking them as deleted and disable all the condtions associated with that

## Related Commands
  * [New-MonitorNotificationPolicy](New-MonitorNotificationPolicy.html)
  * [Get-MonitorNotificationPolicy](Get-MonitorNotificationPolicy.html)
  * [Set-MonitorNotificationRulePolicy](Set-MonitorNotificationRulePolicy.html)
## Parameters

| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| InputObject | Removes all of the instances with the id matching in the specified policy objects | false | true (ByValue) |  |
| Uid | Removes all of the instances with the specified ids.  If any of the ids are invalid, an exception is thrown. | false | false |  |
| LoggingId | Specifies the identifier of the high-level operation this cmdlet call forms a part of. Citrix Studio and Director typically create high-level operations. PowerShell scripts can also wrap a series of cmdlet calls in a high-level operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller the PowerShell snap-in will connect to. You can provide this as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type
### 
   
## Return Values
### Return success if all operations are succeeded
   Return success if all operations are succeeded. An exception is thrown otherwise
## Examples

### EXAMPLE 1
```
Remove-MonitorNotificationPolicy -Id 1
```
   Description<br>-----------<br>Removes the policy with id 1
### EXAMPLE 2
```
Remove-MonitorNotificationPolicy -InputObject $policy
```
   Description<br>-----------<br>Removes the policy with id matching the policy object specified
