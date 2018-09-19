# New-AppLibAppVPackage

   Adds a new package to the library.

## Syntax
```
New-AppLibAppVPackage [-LibraryUid <Int32>] [-Path <String>] [-RetrieveIcon <Boolean>] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
```

## Detailed Description
   The package and the applications that make it up are added to the library.

## Related Commands
  * [Remove-AppLibAppVPackage](Remove-AppLibAppVPackage/)
## Parameters

| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| LibraryUid | The UID of the library to which the package is added. | false | true (ByPropertyName) |  |
| Path | The full path to the package on the network share. | false | true (ByPropertyName) |  |
| RetrieveIcon | A switch to indicate whether to return the package and applications' icon data. | false | false |  |
| LoggingId | Specifies the identifier of the high-level operation this cmdlet call forms a part of. Citrix Studio and Director typically create high-level operations. PowerShell scripts can also wrap a series of cmdlet calls in a high-level operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller the PowerShell snap-in will connect to. You can provide this as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type
### 
   
## Return Values
### Citrix.AppLibrary.Sdk.AppVPackage
   An object representing the details of the the new package.## Notes
   When a package is added to the library and a record of that package already exists, the existing package is updated with the details of the new package. A package is considered as already existing when the following are true: 1) The PackageGuid and VersionGuid are the same as the existing package and the Path is the same or different. 2) The Path is the same as the existing package and the PackageGuid and/or VersionGuid are the same or different.
## Examples

### EXAMPLE 1
```
Add-AppLibAppVPackage -LibraryUid 1 -Path "\\NetworkStorage.enterprise.com\Managed App-V Packages\Package.appv"
```
   Description<br>-----------<br>Adds the package at the specified network location to the library.
