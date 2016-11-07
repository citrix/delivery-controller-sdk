# Remove-MonitorNotificationPolicyEmailAddresses

   Remove email addresses from the existing policy specified and returns the updated policy.

## Syntax
```
Remove-MonitorNotificationPolicyEmailAddresses -InputObject <MonitorNotificationPolicy> -EmailAddresses <String[]> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]

Remove-MonitorNotificationPolicyEmailAddresses -Uid <Int64> -EmailAddresses <String[]> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
```

## Detailed Description
   Remove email addresses from the existing policy specified and returns the updated policy.

## Related Commands
  * [Get-MonitorNotificationPolicy](Get-MonitorNotificationPolicy.html)
  * [Set-MonitorNotificationPolicy](Set-MonitorNotificationPolicy.html)
  * [Remove-MonitorNotificationPolicy](Remove-MonitorNotificationPolicy.html)
## Parameters

| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| InputObject | Specifies the policy object from which the email addresses to be removed | true | true (ByValue) |  |
| EmailAddresses | Collection of email addresses to be removed | true | false |  |
| Uid | Specifies the unique identifier of the policy from which the email addresses to be removed. | true | false |  |
| LoggingId | Specifies the identifier of the high-level operation this cmdlet call forms a part of. Citrix Studio and Director typically create high-level operations. PowerShell scripts can also wrap a series of cmdlet calls in a high-level operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller the PowerShell snap-in will connect to. You can provide this as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type
### 
   
## Return Values
### MonitorNotificationPolicy
   Returns the updated policy object
## Examples

### EXAMPLE 1
```
Remove-MonitorNotificationPolicyEmailAddresses -Uid 100 -EmailAddresses $emailAddresses
```
   Description<br>-----------<br>Removes the email addresses from the policy matching id 100
