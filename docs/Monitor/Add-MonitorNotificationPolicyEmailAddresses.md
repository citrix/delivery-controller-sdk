
# Add-Monitornotificationpolicyemailaddresses
Add email addresses to the existing policy specified and returns the updated policy.
## Syntax
```
Add-MonitorNotificationPolicyEmailAddresses -InputObject <MonitorNotificationPolicy> -EmailAddresses <String[]> -EmailCultureName <String> [-LoggingId <Guid>] [-BearerToken <String>] [-AdminAddress <String>] [<CommonParameters>]

Add-MonitorNotificationPolicyEmailAddresses -Uid <Int64> -EmailAddresses <String[]> -EmailCultureName <String> [-LoggingId <Guid>] [-BearerToken <String>] [-AdminAddress <String>] [<CommonParameters>]
```
## Detailed Description
Add email addresses to the existing policy specified and returns the updated policy.


## Related Commands

* [Get-MonitorNotificationPolicy](./Get-MonitorNotificationPolicy/)
* [Set-MonitorNotificationPolicy](./Set-MonitorNotificationPolicy/)
* [Remove-MonitorNotificationPolicy](./Remove-MonitorNotificationPolicy/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| InputObject | Specifies the policy object to which the conditions to be added. | true | true (ByValue) |  |
| EmailAddresses | Collection of email addresses to be added | true | false |  |
| EmailCultureName | Text encoding of the culture to return the email in | true | false |  |
| Uid | Specifies the unique identifier of the policy to which the conditions to be added. | true | false |  |
| LoggingId | Specifies the identifier of the high-level operation this cmdlet call forms a part of. Citrix Studio and Director typically create high-level operations. PowerShell scripts can also wrap a series of cmdlet calls in a high-level operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller the PowerShell snap-in will connect to. You can provide this as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type

### 

## Return Values

### Collection\[Monitornotificationpolicy\]
Returns the collection of policy objects created
## Examples

### Example 1
```
$emailaddress = @()

          $emailaddress += "user1@abc.com"

          Add-MonitorNotificationPolicyEmailAddresses -Uid 100 -EmailAddresses $emailaddress -EmailCultureName "en-US"
```
#### Description
Add email addresses to the policy matching the id 100
