# Remove-BrokerEntitlementPolicyRule

   Deletes a desktop rule from the site's entitlement policy.

## Syntax
```
Remove-BrokerEntitlementPolicyRule [-InputObject] <EntitlementPolicyRule[]> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]

Remove-BrokerEntitlementPolicyRule [-Name] <String> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
```

## Detailed Description
   The Remove-BrokerEntitlementPolicyRule cmdlet deletes a desktop rule from the site's entitlement policy.

A desktop rule in the entitlement policy defines the users who are allowed per-session access to a machine from the rule's associated desktop group to run a full desktop session.

Deleting a rule does not affect existing sessions launched using the rule, but users cannot reconnect to those sessions if they are subsequently disconnected.

## Related Commands
  * [New-BrokerEntitlementPolicyRule](New-BrokerEntitlementPolicyRule.html)
  * [Get-BrokerEntitlementPolicyRule](Get-BrokerEntitlementPolicyRule.html)
  * [Set-BrokerEntitlementPolicyRule](Set-BrokerEntitlementPolicyRule.html)
  * [Rename-BrokerEntitlementPolicyRule](Rename-BrokerEntitlementPolicyRule.html)
## Parameters

| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| InputObject | The desktop rule to be deleted from the entitlement policy. | true | true (ByValue) |  |
| Name | The name of the desktop rule to be deleted from the entitlement policy. | true | true (ByPropertyName) |  |
| LoggingId | Specifies the identifier of the high level operation that this cmdlet call forms a part of. Desktop Studio and Desktop Director typically create High Level Operations. PowerShell scripts can also wrap a series of cmdlet calls in a High Level Operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |

## Input Type
### Citrix.Broker.Admin.SDK.EntitlementPolicyRule
   The desktop rule to be deleted from the entitlement policy.
## Return Values
### None
   
## Examples

### EXAMPLE 1
```
C:\PS> Remove-BrokerEntitlementPolicyRule 'Temp Workers'
```
   Description<br>-----------<br>Deletes the desktop rule called Temp Workers from the entitlement policy. Existing desktop sessions launched using the rule are not affected, but users cannot reconnect to sessions if they are subsequently disconnected.
### EXAMPLE 2
```
C:\PS> $dg = Get-BrokerDesktopGroup 'Customer Support'
C:\PS> Get-BrokerEntitlementPolicyRule -DesktopGroupUid $dg.Uid | Remove-BrokerEntitlementPolicyRule
```
   Description<br>-----------<br>Deletes all desktop rules from the entitlement policy applying to the Customer Support desktop group. This effectively removes all access to the desktops published from this group. Existing desktop sessions are not affected, but users cannot reconnect to sessions if they are subsequently disconnected.
