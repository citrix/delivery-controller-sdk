# Rename-BrokerApplicationGroup

   Renames an application group.

## Syntax
```
Rename-BrokerApplicationGroup [-InputObject] <ApplicationGroup[]> [-NewName] <String> [-PassThru] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]

Rename-BrokerApplicationGroup [-Name] <String> [-NewName] <String> [-PassThru] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
```

## Detailed Description
   The Rename-BrokerApplicationGroup cmdlet changes the name of an application group. An application group cannot have the same name as another application group.

Application group names are not visible to end users.

## Related Commands
  * [Add-BrokerApplicationGroup](Add-BrokerApplicationGroup.html)
  * [Get-BrokerApplicationGroup](Get-BrokerApplicationGroup.html)
  * [New-BrokerApplicationGroup](New-BrokerApplicationGroup.html)
  * [Remove-BrokerApplicationGroup](Remove-BrokerApplicationGroup.html)
  * [Set-BrokerApplicationGroup](Set-BrokerApplicationGroup.html)
## Parameters

| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| InputObject | Specifies the application group to rename. | true | true (ByValue) | nul |
| Name | Specifies the name of the application group to rename. | true | true (ByPropertyName) | null |
| NewName | Specifies the new name of the application group. | true | false |  |
| PassThru | This cmdlet does not generate any output, unless you use the PassThru parameter, in which case it returns the affected record. | false | false | False |
| LoggingId | Specifies the identifier of the high level operation that this cmdlet call forms a part of. Desktop Studio and Desktop Director typically create High Level Operations. PowerShell scripts can also wrap a series of cmdlet calls in a High Level Operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |

## Input Type
### Citrix.Broker.Admin.SDK.ApplicationGroup
   You can pipe application groups to Rename-BrokerApplicationGroup.
## Return Values
### None or Citrix.Broker.Admin.SDK.ApplicationGroup
   This cmdlet does not generate any output, unless you use the PassThru parameter, in which case it generates a Citrix.Broker.Admin.SDK.ApplicationGroup object.
## Examples

### EXAMPLE 1
```
C:\PS> Rename-BrokerApplicationGroup -Name "Ofice" -NewName "Office"
```
   Description<br>-----------<br>Renames the application group with name "Ofice" to "Office".
### EXAMPLE 2
```
C:\PS> Get-BrokerApplicationGroup -Uid 1 | Rename-BrokerApplicationGroup -NewName "New Name" -PassThru
```
   Description<br>-----------<br>Renames application group with the Uid 1 to "New Name", showing the result.
