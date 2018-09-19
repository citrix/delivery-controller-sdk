# Set-AppLibIsolationGroup

   Updates an isolation group in the library

## Syntax
```
Set-AppLibIsolationGroup [-IsolationGroupUid] <Int32> [-Name <String>] [-Description <String>] [-Version <String>] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
```

## Detailed Description
   The isolation group will be updated with the new properties

## Related Commands
  * [New-AppLibIsolationGroup](New-AppLibIsolationGroup/)
  * [Remove-AppLibIsolationGroup](Remove-AppLibIsolationGroup/)
  * [Set-AppLibIsolationGroupPackage](Set-AppLibIsolationGroupPackage/)
## Parameters

| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| IsolationGroupUid | The AppLibrary's internal unique identifier of the Isolation Group. | true | true (ByPropertyName) |  |
| Name | The name of the isolation group. | false | true (ByPropertyName) |  |
| Description | The description of the isolation group. | false | true (ByPropertyName) |  |
| Version | The version of the isolation group. | false | true (ByPropertyName) |  |
| LoggingId | Specifies the identifier of the high-level operation this cmdlet call forms a part of. Citrix Studio and Director typically create high-level operations. PowerShell scripts can also wrap a series of cmdlet calls in a high-level operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller the PowerShell snap-in will connect to. You can provide this as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type
### 
   
## Return Values
### 
   
## Examples

### EXAMPLE 1
```
Set-AppLibIsolationGroup -IsolationGroupUid 58  -Name "MyIsolationGroup" -Description "Some description here" -Version "1.0.0.1"
```
   Description<br>-----------<br>Updates the specified isolation group with the new properties.
