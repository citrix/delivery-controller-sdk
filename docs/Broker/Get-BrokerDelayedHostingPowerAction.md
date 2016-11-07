# Get-BrokerDelayedHostingPowerAction

   Gets power actions that are executed after a delay.

## Syntax
```
Get-BrokerDelayedHostingPowerAction [-Uid] <Int64> [-Property <String[]>] [-AdminAddress <String>] [<CommonParameters>]

Get-BrokerDelayedHostingPowerAction [[-MachineName] <String>] [-Action <PowerManagementAction>] [-ActionDueTime <DateTime>] [-DNSName <String>] [-HostedMachineName <String>] [-HypervisorConnectionName <String>] [-HypervisorConnectionUid <Int32>] [-ReturnTotalRecordCount] [-MaxRecordCount <Int32>] [-Skip <Int32>] [-SortBy <String>] [-Filter <String>] [-Property <String[]>] [-AdminAddress <String>] [<CommonParameters>]
```

## Detailed Description
   Finds all delayed power actions that match the specified search criteria.


-------------------------- BrokerDelayedHostingPowerAction Object
The BrokerDelayedHostingPowerAction object represents an instance of a power action that is executed after a delay. It contains the following properties:

    -- Action (Citrix.Broker.Admin.SDK.PowerManagementAction)
       The power action to apply to the machine. Possible values are ShutDown and Suspend.

    -- ActionDueTime (System.DateTime)
       The UTC time at which the power action is due to be queued for execution.

    -- DNSName (System.String)
       The fully qualified DNS name of the machine that the power action applies to.

    -- HostedMachineName (System.String)
       The hypervisor's name for the machine that the power action applies to.

    -- HypervisorConnectionUid (System.Int32)
       The unique identifier of the hypervisor connection that is associated with the target machine.

    -- MachineName (System.String)
       The name of the machine that the power action applies to, in the form domain\machine.

    -- Uid (System.Int64)
       The unique identifier of the power action.

## Related Commands
  * [New-BrokerDelayedHostingPowerAction](New-BrokerDelayedHostingPowerAction.html)
  * [Remove-BrokerDelayedHostingPowerAction](Remove-BrokerDelayedHostingPowerAction.html)
  * [Remove-BrokerHostingPowerAction](Remove-BrokerHostingPowerAction.html)
## Parameters

| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| Uid | Gets only the single action record whose ID matches the specified value. | true | false |  |
| MachineName | Gets only the records for actions that are for machines whose name (of the form domain\machine) matches the specified string. | false | false |  |
| Action | Gets only the records for actions with the specified action type.<br>Valid values are Shutdown and Suspend. | false | false |  |
| ActionDueTime | Gets only the records for actions due to be queued for execution at the specified time. This is useful with advanced filtering; for more information, see about_Broker_Filtering. | false | false |  |
| DNSName | Gets only the records for actions that are for machines whose DNS name matches the specified string. | false | false |  |
| HostedMachineName | Gets only the records for actions that are for machines whose Hosting Name (the machine name as understood by the hypervisor) matches the specified string. | false | false |  |
| HypervisorConnectionName | Gets only the records for actions for machines hosted through a hypervisor connection whose name matches the specified string. | false | false |  |
| HypervisorConnectionUid | Gets only the records for actions for machines hosted through a hypervisor connection whose ID matches the specified value. | false | false |  |
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
### Citrix.Broker.Admin.SDK.DelayedHostingPowerAction
   Get-BrokerDelayedHostingPowerAction returns all delayed power actions that match the specified selection criteria.
## Examples

### EXAMPLE 1
```
C:\PS> Get-BrokerDelayedHostingPowerAction
```
   Description<br>-----------<br>Fetches records for all known delayed power actions that have not yet been queued for execution.
