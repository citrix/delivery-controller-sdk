# Remove-BrokerAssignmentPolicyRule

   Deletes a desktop rule from the site's assignment policy.

## Syntax
```
Remove-BrokerAssignmentPolicyRule [-InputObject] <AssignmentPolicyRule[]> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]

Remove-BrokerAssignmentPolicyRule [-Name] <String> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
```

## Detailed Description
   The Remove-BrokerAssignmentPolicyRule cmdlet deletes a desktop rule from the site's assignment policy.

A desktop rule in the assignment policy defines the users who are entitled to self-service persistent machine assignments from the rule's desktop group. A rule defines how many machines a user is allowed from the group for delivery of full desktop sessions.

Deleting a desktop rule does not remove machine assignments that have already been made by the rule, nor does it affect active sessions to those machines in any way.

## Related Commands
  * [New-BrokerAssignmentPolicyRule](New-BrokerAssignmentPolicyRule.html)
  * [Get-BrokerAssignmentPolicyRule](Get-BrokerAssignmentPolicyRule.html)
  * [Set-BrokerAssignmentPolicyRule](Set-BrokerAssignmentPolicyRule.html)
  * [Rename-BrokerAssignmentPolicyRule](Rename-BrokerAssignmentPolicyRule.html)
## Parameters

| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| InputObject | The desktop rule to be deleted from the assignment policy. | true | true (ByValue) |  |
| Name | The name of the desktop rule to be deleted from the assignment policy. | true | true (ByPropertyName) |  |
| LoggingId | Specifies the identifier of the high level operation that this cmdlet call forms a part of. Desktop Studio and Desktop Director typically create High Level Operations. PowerShell scripts can also wrap a series of cmdlet calls in a High Level Operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |

## Input Type
### Citrix.Broker.Admin.SDK.AssignmentPolicyRule
   The desktop rule to be deleted from the assignment policy.
## Return Values
### None
   
## Examples

### EXAMPLE 1
```
C:\PS> Remove-BrokerAssignmentPolicyRule 'Temp Staff'
```
   Description<br>-----------<br>Deletes the desktop rule called Temp Staff from the assignment policy. Access to machines already assigned by this rule is not affected in any way.
### EXAMPLE 2
```
C:\PS> $dg = Get-BrokerDesktopGroup 'Sales Support'
C:\PS> Get-BrokerAssignmentPolicyRule -DesktopGroupUid $dg.Uid | Remove-BrokerAssignmentPolicyRule
```
   Description<br>-----------<br>Deletes all desktop rules for the Sales Support desktop group from the site's assignment policy. This prevents any further machine assignments being made from this group, but it does not affect existing assignments made by these rules.
