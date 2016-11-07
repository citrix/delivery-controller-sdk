# New-BrokerApplicationGroup

   Create a new application group to which applications can be added.

## Syntax
```
New-BrokerApplicationGroup [-Name] <String> [-Description <String>] [-Enabled <Boolean>] [-RestrictToTag <String>] [-Scope <String[]>] [-SessionSharingEnabled <Boolean>] [-TenantId <Guid>] [-UserFilterEnabled <Boolean>] [-UUID <Guid>] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
```

## Detailed Description
   The New-BrokerApplicationGroup cmdlet creates a new application group. Applications that are added to the application group can then be managed centrally by setting properties on the application group rather than on each application individually.

Application groups may also be used to isolate applications that should not share sessions with other applications. To do this, create an application group with SessionSharingEnabled equal to $false, and then add to it those applications that you wish to isolate. The isolated applications continue to share sessions with each other, but not with any other published applications.

To create a new application and add it to an application group, use New-BrokerApplication -ApplicationGroup. To add an existing application to an application group, use Add-BrokerApplication -ApplicationGroup.

After adding applications to an application group, you must then publish the application group to a desktop group before its applications can be launched. Use the Add-BrokerApplicationGroup cmdlet to do this.

To manipulate the user filter associated with an application group, use Add-BrokerUser -ApplicationGroup and Remove-BrokerUser -ApplicationGroup.

To manipulate the set of tags associated with an application group, use Add-BrokerTag -ApplicationGroup and Remove-BrokerTag -ApplicationGroup.

See about_Broker_Applications for more information.

## Related Commands
  * [Add-BrokerApplicationGroup](Add-BrokerApplicationGroup.html)
  * [Get-BrokerApplicationGroup](Get-BrokerApplicationGroup.html)
  * [Remove-BrokerApplicationGroup](Remove-BrokerApplicationGroup.html)
  * [Rename-BrokerApplicationGroup](Rename-BrokerApplicationGroup.html)
  * [Set-BrokerApplicationGroup](Set-BrokerApplicationGroup.html)
  * [Add-BrokerApplication](Add-BrokerApplication.html)
  * [Remove-BrokerApplication](Remove-BrokerApplication.html)
  * [Add-BrokerUser](Add-BrokerUser.html)
  * [Remove-BrokerUser](Remove-BrokerUser.html)
  * [Add-BrokerTag](Add-BrokerTag.html)
  * [Remove-BrokerTag](Remove-BrokerTag.html)
## Parameters

| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| Name | A name for the application group. Not visible to end users. | true | true (ByPropertyName) |  |
| Description | A description for the application group. Not visible to end users. | false | true (ByPropertyName) | null |
| Enabled | Whether the application group's applications can be launched by end users. | false | true (ByPropertyName) | true |
| RestrictToTag | Optional tag that may be used further to restrict which machines may be used for launching the application group's applications. A machine may be used by an application group if either the application group has no tag restriction or the application group does have a tag restriction and the machine is tagged with the same tag. | false | true (ByPropertyName) | null |
| Scope | Specifies the name of the delegated administration scope to which the application group should belong. | false | true (ByPropertyName) | null |
| SessionSharingEnabled | Whether the application group's applications can share sessions with applications that are not a member of this application group. | false | true (ByPropertyName) | true |
| TenantId | Specifies identity of tenant associated with application group. Must always be specified in multitenant sites, must not be specified otherwise. | false | true (ByPropertyName) |  |
| UserFilterEnabled | Whether the application group's user filter is enabled or disabled. Where the user filter is enabled, the application is visible only to users who appear in the filter (either explicitly or by virtue of group membership). | false | true (ByPropertyName) | false |
| UUID | The UUID of the application group. If a UUID is not provided, then one will be generated automatically. | false | true (ByPropertyName) | null |
| LoggingId | Specifies the identifier of the high level operation that this cmdlet call forms a part of. Desktop Studio and Desktop Director typically create High Level Operations. PowerShell scripts can also wrap a series of cmdlet calls in a High Level Operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |

## Input Type
### None
   You cannot pipe input into this cmdlet.
## Return Values
### Citrix.Broker.Admin.SDK.ApplicationGroup
   The newly created application group.
## Examples

### EXAMPLE 1
```
C:\PS> New-BrokerApplicationGroup "Helpdesk Apps"
```
   Description<br>-----------<br>Creates a new application group called 'Helpdesk Apps'.
### EXAMPLE 2
```
C:\PS> New-BrokerApplicationGroup "Accounts Apps" -UserFilterEnabled $true
C:\PS> Add-BrokerUser "MYDOMAIN\Accounts" -ApplicationGroup "Accounts Apps"
```
   Description<br>-----------<br>Creates a new application group called 'Accounts Apps', and then restrict access so that only members of the MYDOMAIN\Accounts user group can launch applications in 'Accounts Apps'.
