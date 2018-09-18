# Remove-BrokerLease

   Remove the specified lease in the Database.

## Syntax
```
Remove-BrokerLease [-InputObject] <Lease[]> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]

Remove-BrokerLease [-Key] <String> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
```

## Detailed Description
   Marks the specified lease for deletion. Note that the lease is eventually fully deleted when enough time has been allowed for the deletion to propagate to all controller machines in the site, but is immediately removed from lease search results.

## Related Commands
  * [Update-BrokerLocalLeaseCache](Update-BrokerLocalLeaseCache/)
  * [Remove-BrokerCache](Remove-BrokerCache/)
## Parameters

| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| InputObject | Specifies the lease to remove. | true | true (ByValue) |  |
| Key | Specifies the lease key of the lease to remove. A pattern can be specified. | true | true (ByPropertyName) |  |
| LoggingId | Specifies the identifier of the high level operation that this cmdlet call forms a part of. Desktop Studio and Desktop Director typically create High Level Operations. PowerShell scripts can also wrap a series of cmdlet calls in a High Level Operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |

## Input Type
### Citrix.Broker.Admin.SDK.Lease
   The lease to be removed can be piped into the cmdlet.
## Return Values
### None
   This cmdlet does not return any output.## Notes
   The lease is marked for deletion after this cmdlet is run. Note that the lease is eventually fully deleted when enough time has been allowed for the deletion to propagate to all controller machines in the site, but is immediately removed from lease search results.
## Examples

### EXAMPLE 1
```
C:\PS> $lease = Get-BrokerLease -Uid 1
C:\PS> Remove-BrokerLease $lease
```
   Description<br>-----------<br>Marks the specified lease for deletion.
