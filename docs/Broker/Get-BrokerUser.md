# Get-BrokerUser

   Gets broker users configured for this site.

## Syntax
```
Get-BrokerUser -SID <String> [-Property <String[]>] [-AdminAddress <String>] [<CommonParameters>]

Get-BrokerUser [[-Name] <String>] [-FullName <String>] [-HomeZoneName <String>] [-HomeZoneUid <Guid>] [-UPN <String>] [-ApplicationGroupUid <Int32>] [-ApplicationUid <Int32>] [-SessionLingerDesktopGroupUid <Int32>] [-SessionPreLaunchDesktopGroupUid <Int32>] [-MachineUid <Int32>] [-PrivateDesktopUid <Int32>] [-ReturnTotalRecordCount] [-MaxRecordCount <Int32>] [-Skip <Int32>] [-SortBy <String>] [-Filter <String>] [-Property <String[]>] [-AdminAddress <String>] [<CommonParameters>]
```

## Detailed Description
   Retrieve broker users matching the specified criteria. If no parameters are specified this cmdlet enumerates all broker users.

For information about advanced filtering options, see about_Broker_Filtering.


-------------------------- BrokerUser Object
The BrokerUser object represents a single instance of an user. It contains the following properties:

    -- FullName (System.String)
       The full name of an user

    -- HomeZoneName (System.String)
       Name of home zone associated with user

    -- HomeZoneUid (System.Guid?)
       Home zone associated with this user

    -- Name (System.String)
       The name of an user

    -- SID (System.String)
       The SID of an user

    -- UPN (System.String)
       The UPN of an user

## Related Commands
  * [Add-BrokerUser](Add-BrokerUser/)
  * [Remove-BrokerUser](Remove-BrokerUser/)
## Parameters

| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| SID | Gets the broker user with the specified SID property value. | true | false |  |
| Name | Gets the broker user with the specified Name property. | false | false |  |
| FullName | Gets the broker user with the specified FullName property. | false | false |  |
| HomeZoneName | Gets user/group accounts having a home zone preference matching the specified name. | false | false |  |
| HomeZoneUid | Gets user/group accounts having a home zone preference matching the specified UID. | false | false |  |
| UPN | Gets the broker user with the specified UPN property value. | false | false |  |
| ApplicationGroupUid | Gets broker users associated with the application group with the specified Uid. | false | false |  |
| ApplicationUid | Gets broker users associated with the application with the specified Uid. | false | false |  |
| SessionLingerDesktopGroupUid | Gets broker users associated with the desktop group session linger settings with the specified Uid. | false | false |  |
| SessionPreLaunchDesktopGroupUid | Gets broker users associated with the desktop group session pre-launch settings with the specified Uid. | false | false |  |
| MachineUid | Gets broker users associated with the broker machine with the specified Uid. | false | false |  |
| PrivateDesktopUid | Gets broker users associated with the private desktop with the specified Uid. | false | false |  |
| ReturnTotalRecordCount | When specified, this causes the cmdlet to output an error record containing the number of records available. This error record is additional information and does not affect the objects written to the output pipeline. See about_Broker_Filtering for details. | false | false | False |
| MaxRecordCount | Specifies the maximum number of records to return. | false | false | 250 |
| Skip | Skips the specified number of records before returning results. Also reduces the count returned by -ReturnTotalRecordCount. | false | false | 0 |
| SortBy | Sorts the results by the specified list of properties. The list is a set of property names separated by commas, semi-colons, or spaces. Optionally, prefix each name with a + or - to indicate ascending or descending order. Ascending order is assumed if no prefix is present. | false | false | The default sort order is by name or unique identifier. |
| Filter | Gets records that match a PowerShell style filter expression. See about_Broker_Filtering for details. | false | false |  |
| Property | Specifies the properties to be returned. This is similar to piping the output of the command through Select-Object, but the properties are filtered more efficiently at the server. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |

## Input Type
### None
   You cannot pipe input into this cmdlet.
## Return Values
### Citrix.Broker.Admin.SDK.User
   Get-BrokerUser returns an object for each matching broker user.
## Examples

### EXAMPLE 1
```
Get-BrokerUser DOMAIN7\*
```
   Description<br>-----------<br>Get all broker user objects with names matching the supplied pattern
### EXAMPLE 2
```
$pdt = Get-BrokerPrivateDesktop DOMAIN\MACHINENAME\n
              Get-BrokerUser -PrivateDesktopUid $pdt.Uid
```
   Description<br>-----------<br>Get all broker user objects added to the specified private desktop
