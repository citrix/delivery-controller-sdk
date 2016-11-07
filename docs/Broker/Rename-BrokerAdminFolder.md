# Rename-BrokerAdminFolder

   Renames a folder

## Syntax
```
Rename-BrokerAdminFolder [-InputObject] <AdminFolder[]> [-NewName] <String> [-PassThru] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]

Rename-BrokerAdminFolder [-Name] <String> [-NewName] <String> [-PassThru] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
```

## Detailed Description
   The Rename-BrokerAdminFolder cmdlet renames a folder for organising objects for administration purposes (for example, Applications).

The following special characters are not allowed in the new FolderName: \ / ; : # . * ? = < > | [ ] ( ) " ' `

## Related Commands
  * [Get-BrokerAdminFolder](Get-BrokerAdminFolder.html)
  * [New-BrokerAdminFolder](New-BrokerAdminFolder.html)
## Parameters

| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| InputObject | The folder(s) to be renamed | true | true (ByValue) |  |
| Name | A pattern matching the names of folders to be renamed | true | true (ByPropertyName) |  |
| NewName | The name the new folder(s) should have. | true | false |  |
| PassThru | This cmdlet does not generate any output, unless you use the PassThru parameter, in which case it returns the affected record. | false | false | False |
| LoggingId | Specifies the identifier of the high level operation that this cmdlet call forms a part of. Desktop Studio and Desktop Director typically create High Level Operations. PowerShell scripts can also wrap a series of cmdlet calls in a High Level Operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |

## Input Type
### Depends on parameter
   Parameters can be piped by property name.
## Return Values
### None or Citrix.Broker.Admin.SDK.AdminFolder
   This cmdlet does not generate any output, unless you use the PassThru parameter, in which case it generates a Citrix.Broker.Admin.SDK.AdminFolder object.
## Examples

### EXAMPLE 1
```
Rename-BrokerAdminFolder F1\XXX\ YYY
```
   Description<br>-----------<br>Renames the folder called XXX within the folder F1\ to YYY
