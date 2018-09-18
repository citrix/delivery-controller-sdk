# Remove-MonitorNotificationPolicyTargets

   Remove targets from the existing policy specified and returns the updated policy.

## Syntax
```
Remove-MonitorNotificationPolicyTargets -InputObject <MonitorNotificationPolicy> -TargetIds <String[]> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]

Remove-MonitorNotificationPolicyTargets -Uid <Int64> -TargetIds <String[]> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
```

## Detailed Description
   Remove targets from the existing policy specified and returns the updated policy.

## Related Commands
  * [Get-MonitorNotificationPolicy](Get-MonitorNotificationPolicy/)
  * [Set-MonitorNotificationPolicy](Set-MonitorNotificationPolicy/)
  * [Remove-MonitorNotificationPolicy](Remove-MonitorNotificationPolicy/)
## Parameters

| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| InputObject | Specifies the policy object from the targets to be removed | true | true (ByValue) |  |
| TargetIds | Object reference to the array of target ids. Site GUID - for target type Site DesktopGroup UUID - for DesktopGroup, RdsWorker target types | true | false |  |
| Uid | Specifies the unique identifier of the policy from the targets to be removed | true | false |  |
| LoggingId | Specifies the identifier of the high-level operation this cmdlet call forms a part of. Citrix Studio and Director typically create high-level operations. PowerShell scripts can also wrap a series of cmdlet calls in a high-level operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller the PowerShell snap-in will connect to. You can provide this as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type
### 
   
## Return Values
### MonitorNotificationPolicy
   Returns the policy object
## Examples

### EXAMPLE 1
```
$targetIds = @()
          $targetIds += "766cde70-3c69-4481-a658-4e11247ac70d"
          
          Remove-MonitorNotificationPolicyTargets -Uid 100  -TargetIds $targetIds
```
   Description<br>-----------<br>Removes the targets from policy matching id 100
