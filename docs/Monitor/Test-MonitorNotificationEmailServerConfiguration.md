
# Test-Monitornotificationemailserverconfiguration
FIXME
## Syntax
```
Test-MonitorNotificationEmailServerConfiguration [-InputObject] <MonitorNotificationEmailServerConfiguration> -EmailAddresses <String[]> [-Credential <PSCredential>] [-LoggingId <Guid>] [-BearerToken <String>] [-AdminAddress <String>] [<CommonParameters>]

Test-MonitorNotificationEmailServerConfiguration -ProtocolType <EmailProtocolType> -ServerName <String> -PortNumber <Int32> -SenderEmailAddress <String> -RequiresAuthentication <Boolean> -EmailAddresses <String[]> [-Credential <PSCredential>] [-LoggingId <Guid>] [-BearerToken <String>] [-AdminAddress <String>] [<CommonParameters>]

Test-MonitorNotificationEmailServerConfiguration -EmailAddresses <String[]> [-LoggingId <Guid>] [-BearerToken <String>] [-AdminAddress <String>] [<CommonParameters>]
```
## Detailed Description
FIXME


## Related Commands

* [Get-MonitorNotificationEmailServerConfiguration](./Get-MonitorNotificationEmailServerConfiguration/)
* [Set-MonitorNotificationEmailServerConfiguration](./Set-MonitorNotificationEmailServerConfiguration/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| InputObject | Configuration object to test | true | false |  |
| EmailAddresses | Email addresses to which the test mail to be sent | true | true (ByValue) |  |
| ProtocolType | Email protocol Possible values are Smtp SmtpSsl SmtpTls | true | false |  |
| ServerName | Email server name | true | false |  |
| PortNumber | Email server port number | true | false |  |
| SenderEmailAddress | Sender’s email address | true | false |  |
| RequiresAuthentication | Whether the server requires authentication | true | false |  |
| Credential | Configuration credential | false | false |  |
| LoggingId | Specifies the identifier of the high-level operation this cmdlet call forms a part of. Citrix Studio and Director typically create high-level operations. PowerShell scripts can also wrap a series of cmdlet calls in a high-level operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller the PowerShell snap-in will connect to. You can provide this as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type

### 

## Return Values

### System.Boolean
True - when test mail is successfully sent, otherwise false
## Examples

### Example 1
```
$secpasswd = ConvertTo-SecureString "PasswordHere" -AsPlainText -Force

          $mycreds = New-Object System.Management.Automation.PSCredential ("username", $secpasswd)

          Test-MonitorNotificationEmailServerConfiguration -ProtocolType Smtp -ServerName "mail.abc.com" -PortNumber 25 -SenderEmailAddress "user1@citrix.com" -RequiresAuthentication $true -EmailAddresses "user2@abc.com" -Credential $mycreds
```
#### Description
Test whether email can be sent using the specified oncfiguration
