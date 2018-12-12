# Set-ConfigEdgeServer

   Changes the properties of an edge server

## Syntax
```
Set-ConfigEdgeServer [-InputObject] <EdgeServer[]> [-Description <String>] [-MachineAddress <String>] [-Sid <String>] [-Uuid <Guid>] [-ZoneUid <Guid>] [-PassThru] [-LoggingId <Guid>] [-BearerToken <String>] [-AdminAddress <String>] [<CommonParameters>]

Set-ConfigEdgeServer [-Uid] <Guid[]> [-Description <String>] [-MachineAddress <String>] [-Sid <String>] [-Uuid <Guid>] [-ZoneUid <Guid>] [-PassThru] [-LoggingId <Guid>] [-BearerToken <String>] [-AdminAddress <String>] [<CommonParameters>]

Set-ConfigEdgeServer [-Name] <String[]> [-Description <String>] [-MachineAddress <String>] [-Sid <String>] [-Uuid <Guid>] [-ZoneUid <Guid>] [-PassThru] [-LoggingId <Guid>] [-BearerToken <String>] [-AdminAddress <String>] [<CommonParameters>]
```

## Detailed Description
   The Set-ConfigEdgeServer cmdlet sets properties of an edge server or a set of edge servers. The edge server can be specified by name or by one or more edge server instances can be passed to the command either by piping or by using the -InputObject parameter

## Related Commands
  * [New-ConfigEdgeServer](New-ConfigEdgeServer.html)
  * [Get-ConfigEdgeServer](Get-ConfigEdgeServer.html)
  * [Rename-ConfigEdgeServer](Rename-ConfigEdgeServer.html)
  * [Remove-ConfigEdgeServer](Remove-ConfigEdgeServer.html)
## Parameters

| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| InputObject | Specifies the edge server objects to modify. | true | true (ByValue) |  |
| Uid | Identifies the edge server to modify by its UID property. | true | true (ByPropertyName) |  |
| Name | Identifies the edge server to modify by name. | true | true (ByPropertyName) |  |
| Description | Supplies the new value of the Description property. | false | false |  |
| MachineAddress | Supplies the new value of the MachineAddress property. | false | false |  |
| Sid | Supplies the new value of the SID property. | false | false |  |
| Uuid | Supplies the new value of the Uuid property. | false | false |  |
| ZoneUid | Allows moving the edge server to a new zone | false | false |  |
| PassThru | Returns the affected record. By default, this cmdlet does not generate any output. | false | false | False |
| LoggingId | Specifies the identifier of the high-level operation this cmdlet call forms a part of. Citrix Studio and Director typically create high-level operations. PowerShell scripts can also wrap a series of cmdlet calls in a high-level operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller the PowerShell snap-in will connect to. You can provide this as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type
### Citrix.Configuration.Sdk.EdgeServer
   You can pipe the edge servers to be updated into this command.
## Return Values
### None or Citrix.Configuration.Sdk.EdgeServer
   This cmdlet does not generate any output, unless you use the PassThru parameter, in which case it generates a Citrix.Configuration.Sdk.EdgeServer object.
## Examples

### EXAMPLE 1
```
C:\PS> Set-ConfigEdgeServer EdgeSrv1 -ZoneUid d8fe27fa-f33c-47ee-b6b5-80241f536164
```
   Description<br>-----------<br>Associates the edge server 'EdgeSrv1' to a zone specified by its UID
