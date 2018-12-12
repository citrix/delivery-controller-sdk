
# Set-Monitornotificationemailserverconfiguration
Saves a new email server configuration
## Syntax
```
Set-MonitorNotificationEmailServerConfiguration [-InputObject] <MonitorNotificationEmailServerConfiguration> [-LoggingId <Guid>] [-BearerToken <String>] [-AdminAddress <String>] [<CommonParameters>]

Set-MonitorNotificationEmailServerConfiguration -ProtocolType <EmailProtocolType> -ServerName <String> -PortNumber <Int32> -SenderEmailAddress <String> -RequiresAuthentication <Boolean> [-Credential <PSCredential>] [-LoggingId <Guid>] [-BearerToken <String>] [-AdminAddress <String>] [<CommonParameters>]
```
## Detailed Description
The saved configuration describes the new settings to be used to send emails


## Related Commands

* [Get-MonitorNotificationEmailServerConfiguration](./Get-MonitorNotificationEmailServerConfiguration/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| InputObject | Configuration object to persist | true | false |  |
| ProtocolType | Email protocol type. Possible values are Smtp SmtpSsl SmtpTls | true | false |  |
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

### Monitornotificationemailserverconfiguration
The saved configuration
## Examples

### Example 1
```
$secpasswd = ConvertTo-SecureString "PasswordHere" -AsPlainText -Force

          $mycreds = New-Object System.Management.Automation.PSCredential ("username", $secpasswd)

          Set-MonitorNotificationEmailServerConfiguration -ProtocolType Smtp -ServerName "mail.citrix.com" -PortNumber 1111 -SenderEmailAddress "user1@abc.com" -RequiresAuthentication $true -Credential $mycreds
```
#### Description
Set new email server configration using the specified parameters
