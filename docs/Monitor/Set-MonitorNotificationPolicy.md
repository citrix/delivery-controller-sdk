# Set-MonitorNotificationPolicy

   Set/Modify MonitorNotificationPolicy object

## Syntax
```
Set-MonitorNotificationPolicy -InputObject <MonitorNotificationPolicy> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]

Set-MonitorNotificationPolicy -Uid <Int64> [-Name <String>] [-Description <String>] [-Webhook <String>] [-IsSnmpEnabled <Boolean>] [-Enabled <Boolean>] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
```

## Detailed Description
   Returns a new policy instance using the specified parameters

## Related Commands
  * [Get-MonitorNotificationPolicy](Get-MonitorNotificationPolicy/)
  * [New-MonitorNotificationPolicy](New-MonitorNotificationPolicy/)
  * [Remove-MonitorNotificationPolicy](Remove-MonitorNotificationPolicy/)
## Parameters

| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| InputObject | Specifies the new policy object to adjust. | true | false |  |
| Uid | Unique identifier for policy to bet set. | true | false |  |
| Name | New Name of the policy. | false | false |  |
| Description | String value representing the new Policy description | false | false |  |
| Webhook | String value representing the new Policy webhook | false | false |  |
| IsSnmpEnabled | boolean value representing if SNMP is enabled for new Policy | false | false |  |
| Enabled | Boolean paramter indicating the enabled state of the policy. true – Enabled, false – Disabled | false | false |  |
| LoggingId | Specifies the identifier of the high-level operation this cmdlet call forms a part of. Citrix Studio and Director typically create high-level operations. PowerShell scripts can also wrap a series of cmdlet calls in a high-level operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller the PowerShell snap-in will connect to. You can provide this as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type
### 
   
## Return Values
### MonitorNotificationPolicy
   Returns the modified policy
## Examples

### EXAMPLE 1
```
Set-MonitorNotificationPolicy -Id 1 -Enable
```
   Description<br>-----------<br>Enable the policy with the id 1
### EXAMPLE 2
```
$policy = Get-MonitorNotificationPolicy -Uid 1

          $policy.EmailAddresses += "newemail@abc.com"

          Set-MonitorNotificationPolicy -InputObject $policy
```
   Description<br>-----------<br>Update the policy with the id 1 to add new email address
### EXAMPLE 3
```
$policy = Get-MonitorNotificationPolicy -Uid 1
          $policy.TargetIds += "766cde70-3c69-4481-a658-4e11247ac70c"

          $Policy = Set-MonitorNotificationPolicy -Id 1 -InputObject $policy
```
   Description<br>-----------<br>Update the policy with the id 1 to add new target value
