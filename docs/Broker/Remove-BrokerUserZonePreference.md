# Remove-BrokerUserZonePreference

   Removes any zone preference associated with a user/group account in this site

## Syntax
```
Remove-BrokerUserZonePreference [-InputObject] <UserZonePreference[]> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]

Remove-BrokerUserZonePreference [-Name] <String> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
```

## Detailed Description
   The Remove-BrokerUserZonePreference cmdlet removes any preferred home zone associated with a user/group account.

Removing a home preference means that the account no longer has an influence on any choice of zone used for resource launches.

## Related Commands
## Parameters

| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| InputObject | The account zone preference to be removed. | true | true (ByValue) |  |
| Name | The name of the user/group account whose home zone preference is to be removed. | true | true (ByPropertyName) |  |
| LoggingId | Specifies the identifier of the high level operation that this cmdlet call forms a part of. Desktop Studio and Desktop Director typically create High Level Operations. PowerShell scripts can also wrap a series of cmdlet calls in a High Level Operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |

## Input Type
### Citrix.Broker.Admin.SDK.UserZonePreference
   The account zone preference to be removed.
## Return Values
### None
   
## Examples

### EXAMPLE 1
```
Remove-BrokerUserZonePreference APAC\sales
```
   Description<br>-----------<br>Removes any home zone preference associated with the APAC\sales account for this site.
