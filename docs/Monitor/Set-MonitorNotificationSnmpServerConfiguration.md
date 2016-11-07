# Set-MonitorNotificationSnmpServerConfiguration

   Saves a new Snmp server configuration

## Syntax
```
Set-MonitorNotificationSnmpServerConfiguration [-InputObject] <MonitorNotificationSnmpServerConfiguration> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]

Set-MonitorNotificationSnmpServerConfiguration [-ServerName <String>] [-PortNumber <Int32>] [-SnmpSender <String>] [-EngineId <String>] [-AuthPassword <SecureString>] [-PrivPassword <SecureString>] [-PrivPasswordProtocol <PrivacyProtocolType>] [-AuthPasswordProtocol <AuthProtocolType>] [-CommunityString <String>] [-Protocol <SnmpProtocolType>] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
```

## Detailed Description
   The saved configuration describes the new settings to be used to send Snmps

## Related Commands
  * [Get-MonitorNotificationSnmpServerConfiguration](Get-MonitorNotificationSnmpServerConfiguration.html)
## Parameters

| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| InputObject | Configuration object to persist | true | false |  |
| ServerName | Snmp listener server name | false | false |  |
| PortNumber | Snmp server port number | false | false |  |
| SnmpSender | Sender’s Name | false | false |  |
| EngineId | Engine ID | false | false |  |
| AuthPassword | Password used for authentication | false | false |  |
| PrivPassword | Password used for encryption | false | false |  |
| PrivPasswordProtocol | Protocol used for encryption | false | false |  |
| AuthPasswordProtocol | Protocol used for hash Authentication | false | false |  |
| CommunityString | Comunity String for SNMP V2 | false | false |  |
| Protocol | Snmp protocol used for trap | false | false |  |
| LoggingId | Specifies the identifier of the high-level operation this cmdlet call forms a part of. Citrix Studio and Director typically create high-level operations. PowerShell scripts can also wrap a series of cmdlet calls in a high-level operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller the PowerShell snap-in will connect to. You can provide this as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type
### 
   
## Return Values
### MonitorNotificationSnmpServerConfiguration
   The saved configuration
## Examples

### EXAMPLE 1
```
Set-MonitorNotificationSnmpServerConfiguration -ServerName "192.168.100.100" -PortNumber 162 -SnmpSender directoradmin -AuthPassword authpassword -AuthPasswordProtocol MD5 -PrivatePassword PrivPassword -PrivatePasswordProtocol DES
```
   Description<br>-----------<br>Set new Snmp server configration using the specified parameters
