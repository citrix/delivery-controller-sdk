# Rename-ConfigEdgeServer

   Renames an edge server

## Syntax
```
Rename-ConfigEdgeServer [-InputObject] <EdgeServer> [-NewName] <String> [-PassThru] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]

Rename-ConfigEdgeServer [-Uid] <Guid> [-NewName] <String> [-PassThru] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]

Rename-ConfigEdgeServer [-Name] <String> [-NewName] <String> [-PassThru] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
```

## Detailed Description
   The Rename-ConfigEdgeServer cmdlet changes the name of an edge server. All edge servers in a site must have a unique name.

The following special characters are not allowed in the name: \ / ; : # . * ? = < > | [ ] ( ) " ' `

## Related Commands
  * [New-ConfigEdgeServer](New-ConfigEdgeServer.html)
  * [Set-ConfigEdgeServer](Set-ConfigEdgeServer.html)
  * [Get-ConfigEdgeServer](Get-ConfigEdgeServer.html)
  * [Remove-ConfigEdgeServer](Remove-ConfigEdgeServer.html)
## Parameters

| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| InputObject | Specifies the edge server to rename | true | true (ByValue) |  |
| Uid | Specifies the UID of the edge server to rename | true | true (ByPropertyName) |  |
| Name | Specifies the name of the edge server to rename | true | true (ByPropertyName) |  |
| NewName | Specifies the new name of the edge server | true | false |  |
| PassThru | Returns the affected record. By default, this cmdlet does not generate any output. | false | false | False |
| LoggingId | Specifies the identifier of the high-level operation this cmdlet call forms a part of. Citrix Studio and Director typically create high-level operations. PowerShell scripts can also wrap a series of cmdlet calls in a high-level operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller the PowerShell snap-in will connect to. You can provide this as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type
### Citrix.Configuration.Sdk.EdgeServer
   You can pipe edge servers to Rename-ConfigEdgeServer.
## Return Values
### None or Citrix.Configuration.Sdk.EdgeServer
   This cmdlet does not generate any output, unless you use the PassThru parameter, in which case it generates a Citrix.Configuration.Sdk.EdgeServer object.
## Examples

### EXAMPLE 1
```
C:\PS> Rename-ConfigEdgeServer -Name "Old name" -NewName "New Name"
```
   Description<br>-----------<br>Renames the edge server with the name "Old name" to "New Name"
### EXAMPLE 2
```
C:\PS>  Get-ConfigEdgeServer "Old name" | Rename-ConfigEdgeServer -NewName "New name"
```
   Description<br>-----------<br>Renames the edge server with the name "Old name" to "New Name"
