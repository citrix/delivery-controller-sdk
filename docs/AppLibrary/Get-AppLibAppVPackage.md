# Get-AppLibAppVPackage

   Gets the details of an App-V package held in the application library.

## Syntax
```
Get-AppLibAppVPackage [[-Uid] <Int32>] [-Name <String>] [-LibraryUid <Int32>] [-Description <String>] [-RetrieveIcon <Boolean>] [-Property <String[]>] [-ReturnTotalRecordCount] [-MaxRecordCount <Int32>] [-Skip <Int32>] [-SortBy <String>] [-Filter <String>] [-AdminAddress <String>] [<CommonParameters>]
```

## Detailed Description
   The application library holds the information about App-V packages, their location on the network, and the applications they contain.

## Related Commands
## Parameters

| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| Uid | The AppLibrary's internal UID of the App-V package. | false | true (ByPropertyName) |  |
| Name | The name of the App-V package. | false | true (ByPropertyName) |  |
| LibraryUid | The AppLibrary's internal UID of the specific library that holds details of the App-V package. | false | true (ByPropertyName) |  |
| Description | A description of the App-V package and its contents. | false | false |  |
| RetrieveIcon | A switch to indicate whether to return the package's icon data. | false | false |  |
| Property | Specifies the properties to be returned. This is similar to piping the output of the command through Select-Object, but the properties are filtered more efficiently at the server. | false | false |  |
| ReturnTotalRecordCount | When specified, the cmdlet outputs an error record containing the number of records available. This error record is additional information and does not affect the objects written to the output pipeline. See about_AppLib_Filtering for details. | false | false | False |
| MaxRecordCount | Specifies the maximum number of records to return. | false | false | 250 |
| Skip | Skips the specified number of records before returning results. Also reduces the count returned by -ReturnTotalRecordCount. | false | false | 0 |
| SortBy | Sorts the results by the specified list of properties. The list is a set of property names separated by commas, semi-colons, or spaces. Optionally, prefix each name with a + or - to indicate ascending or descending order. Ascending order is assumed if no prefix is present. | false | false | The default sort order is by name or unique identifier. |
| Filter | Gets records that match a PowerShell-style filter expression. See about_AppLib_Filtering for details. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller the PowerShell snap-in will connect to. You can provide this as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type
### 
   
## Return Values
### Citrix.AppLibrary.Sdk.AppVPackage
   An object representing the details needed to identify an App-V package.## Notes
   Pass in the App-V package's UID to retrieve a single App-V package.<br>    Pass in a library UID to retrieve all of the packages in that library.<br>    Call the cmdlet without any parameters to retrieve all of the packages in the AppLibrary.
## Examples

### EXAMPLE 1
```
Get-AppLibAppVPackage
```
   Description<br>-----------<br>Gets the details of all of the App-V packages in the AppLibrary.
### EXAMPLE 2
```
Get-AppLibAppVPackage -Name "MyPackage"
```
   Description<br>-----------<br>Gets the details of the App-V package named MyPackage.
### EXAMPLE 3
```
Get-AppLibAppVPackage -libraryUid 1
```
   Description<br>-----------<br>Gets the details of all of the App-V packages in the specified library.
