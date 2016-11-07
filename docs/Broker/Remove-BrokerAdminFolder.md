# Remove-BrokerAdminFolder

   Removes an admin folder.

## Syntax
```
Remove-BrokerAdminFolder [-InputObject] <AdminFolder[]> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]

Remove-BrokerAdminFolder [-Name] <String> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
```

## Detailed Description
   The Remove-BrokerAdminFolder cmdlet removes an existing admin folder.

Remove-BrokerAdminFolder will not remove a folder if it contains any other objects (e.g. sub-folders or applications).

## Related Commands
  * [Get-BrokerAdminFolder](Get-BrokerAdminFolder.html)
  * [New-BrokerAdminFolder](New-BrokerAdminFolder.html)
## Parameters

| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| InputObject | Identifies the folder to remove | true | true (ByValue) |  |
| Name | The name pattern of folder(s) to remove | true | true (ByPropertyName) |  |
| LoggingId | Specifies the identifier of the high level operation that this cmdlet call forms a part of. Desktop Studio and Desktop Director typically create High Level Operations. PowerShell scripts can also wrap a series of cmdlet calls in a High Level Operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |

## Input Type
### Citrix.Broker.Admin.SDK.AdminFolder
   The admin folder objects can be specified as input.
## Return Values
### None
   This cmdlet does not return any output.
## Examples

### EXAMPLE 1
```
Remove-BrokerAdminFolder F1\F2\
```
   Description<br>-----------<br>Removes the folder called F2 within the folder F1\
