# Move-BrokerAdminFolder

   Moves a folder to another place in the hierarchy, optionally renaming it

## Syntax
```
Move-BrokerAdminFolder [-InputObject] <AdminFolder[]> [-Destination] <AdminFolder> [-NewName <String>] [-PassThru] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]

Move-BrokerAdminFolder [-Name] <String> [-Destination] <AdminFolder> [-NewName <String>] [-PassThru] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
```

## Detailed Description
   The Move-BrokerAdminFolder cmdlet moves a folder for organising objects for administration purposes (for example, Applications) to another position in the hierarchy.

The following special characters are not allowed in the new FolderName: \ / ; : # . * ? = < > | [ ] ( ) " ' `

## Related Commands
  * [Get-BrokerAdminFolder](Get-BrokerAdminFolder.html)
  * [New-BrokerAdminFolder](New-BrokerAdminFolder.html)
## Parameters

| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| InputObject | The folder(s) to be moved | true | true (ByValue) |  |
| Name | A pattern matching the names of folders to be moved | true | true (ByPropertyName) |  |
| Destination | The destination folder the folder being moved should end up in | true | false |  |
| NewName | The name the new folder should have in the destination folder | false | false |  |
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
Move-BrokerAdminFolder F1\XXX\ F2\
```
   Description<br>-----------<br>Moves the folder called XXX within the folder F1\ to a new home in F2\
### EXAMPLE 2
```
Move-BrokerAdminFolder F1\XXX\ F2\ -NewName YYY
```
   Description<br>-----------<br>Moves the folder called XXX within the folder F1\ to a new home in F2\ renaming it to YYY in the process
