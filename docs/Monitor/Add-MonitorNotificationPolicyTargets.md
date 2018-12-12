
# Add-Monitornotificationpolicytargets
Add targets to the existing policy specified and returns the updated policy
## Syntax
```
Add-MonitorNotificationPolicyTargets -InputObject <MonitorNotificationPolicy> -TargetIds <String[]> [-Scope <String>] [-TargetKind <TargetKind>] [-LoggingId <Guid>] [-BearerToken <String>] [-AdminAddress <String>] [<CommonParameters>]

Add-MonitorNotificationPolicyTargets -Uid <Int64> -TargetIds <String[]> [-Scope <String>] [-TargetKind <TargetKind>] [-LoggingId <Guid>] [-BearerToken <String>] [-AdminAddress <String>] [<CommonParameters>]
```
## Detailed Description
Add targets to the existing policy specified and returns the updated policy


## Related Commands

* [Get-MonitorNotificationPolicy](./Get-MonitorNotificationPolicy/)
* [Set-MonitorNotificationPolicy](./Set-MonitorNotificationPolicy/)
* [Remove-MonitorNotificationPolicy](./Remove-MonitorNotificationPolicy/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| InputObject | Specifies the policy object to which the targets to be added | true | true (ByValue) |  |
| TargetIds | Object reference to the array of target ids. Site GUID - for target type Site, DesktopGroup UUID - for DesktopGroup, RdsWorker target types, User SID - for User target type | true | false |  |
| Uid | Specifies the unique identifier of the policy to which the targets to be added | true | false |  |
| Scope | Description of the collection of target ids | false | false |  |
| TargetKind | String representation of the target type enum. Possible values are Site DesktopGroup RdsWorker User | false | false |  |
| LoggingId | Specifies the identifier of the high-level operation this cmdlet call forms a part of. Citrix Studio and Director typically create high-level operations. PowerShell scripts can also wrap a series of cmdlet calls in a high-level operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller the PowerShell snap-in will connect to. You can provide this as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type

### 

## Return Values

### Monitornotificationpolicy
Returns the policy object
## Examples

### Example 1
```
$targetIds = @()

          $targetIds += "766cde70-3c69-4481-a658-4e11247ac70c"

          Add-MonitorNotificationPolicyTargets -Uid 100 -Scope "My Test Targets" -TargetKind Site -TargetIds $targetIds
```
#### Description
Add targets to the policy matching the id 100
