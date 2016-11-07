# New-AppLibAppVPackageRepositoryEvent

   Records telemetry information

## Syntax
```
New-AppLibAppVPackageRepositoryEvent [-RepositoryType <Int32>] [-PackageCount <Int32>] [-Location <String>] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
```

## Detailed Description
   Indicates that an App-V package repository is added to Citrix Studio.

## Related Commands
  * [FIXME](FIXME.html)
  * [FIXME](FIXME.html)
## Parameters

| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| RepositoryType | Indicates the source location of the application | false | false | None - This is a mandatory parameter |
| PackageCount | The number of packages in the repository | false | false | None - This is a mandatory parameter |
| Location | The location(URL) of the App-v package repository | false | false | None - This is a mandatory parameter |
| LoggingId | Specifies the identifier of the high-level operation this cmdlet call forms a part of. Citrix Studio and Director typically create high-level operations. PowerShell scripts can also wrap a series of cmdlet calls in a high-level operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller the PowerShell snap-in will connect to. You can provide this as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type
### 
   
## Return Values
### System.Guid
   Unique identifier for this repository source## Notes
   Telemetry information is sent annonymously to CEIP(Customer Experiance Improvement Program) when the user has opted into the service.<br>    Only the information specified in the parameters are sent to CEIP<br>    RepositoryTypeValue(0) = Microsoft App-V Server<br>    RepositoryTypeValue(1) = Citrix AppLibrary
## Examples

### EXAMPLE 1
```
New-AppLibAppVPackageRepositoryEventCommand -RepositoryType 1 -PackageCount 32 -Location "http://appvserver.acme.com:9000"
```
   Description<br>-----------<br>Records that a Microsoft App-V Server was used in Citrix Studio and that it contains 32 packages located at "http://appvserver.acme.com:9000"
### EXAMPLE 2
```
New-AppLibAppVPackageRepositoryEventCommand -RepositoryType 2 -PackageCount 32 -Location "AppLibrary"
```
   Description<br>-----------<br>Records that the internal Citrix AppLibrary was used in Citrix Studio and that it contains 32 packages.
