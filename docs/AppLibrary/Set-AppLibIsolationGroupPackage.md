# Set-AppLibIsolationGroupPackage

   Updates an App-V package's settings in an Isolation Group.

## Syntax
```
Set-AppLibIsolationGroupPackage [-IsolationGroupUid] <Int32> -AppVPackageUid <Int32> -OrderNumber <Int32> -ExplicitInclusion <Boolean> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
```

## Detailed Description
   Updates an App-V package's settings in the specified Isolation Group.

## Related Commands
  * [Remove-AppLibIsolationGroupPackage](Remove-AppLibIsolationGroupPackage.html)
## Parameters

| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| IsolationGroupUid | The AppLibrary's internal unique identifier of the Isolation Group to contain the package. | true | true (ByPropertyName) |  |
| AppVPackageUid | The AppLibrary's internal unique identifier of the App-V package. | true | true (ByPropertyName) |  |
| OrderNumber | The order number within the Isolation Group. | true | true (ByPropertyName) |  |
| ExplicitInclusion | Indicates whether the package is explicitly included in the delivery group. | true | true (ByPropertyName) |  |
| LoggingId | Specifies the identifier of the high-level operation this cmdlet call forms a part of. Citrix Studio and Director typically create high-level operations. PowerShell scripts can also wrap a series of cmdlet calls in a high-level operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller the PowerShell snap-in will connect to. You can provide this as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type
### 
   
## Return Values
### None
   
## Examples

### EXAMPLE 1
```
Set-AppLibIsolationGroupPackage -IsolationGroupUid 4 -AppVPackageUid 15 -OrderNumber 1 -ExplicitInclusion True
```
   Description<br>-----------<br>Updates the App-V package with the unique identifier in the specified isolation group.
