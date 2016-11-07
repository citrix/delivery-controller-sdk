# Get-AdminScope

   Gets scopes configured for this site.

## Syntax
```
Get-AdminScope [[-Name] <String>] [-Id <Guid>] [-BuiltIn <Boolean>] [-Description <String>] [-Metadata <String>] [-Property <String[]>] [-ReturnTotalRecordCount] [-MaxRecordCount <Int32>] [-Skip <Int32>] [-SortBy <String>] [-Filter <String>] [-AdminAddress <String>] [<CommonParameters>]
```

## Detailed Description
   Retrieves scopes matching the specified criteria. If no parameters are specified this cmdlet enumerates all scopes.

There is one special built-in scope, the 'All' scope.

To determine what objects are currently in a scope, use the Get-<Prefix>ScopedObject from each of the relevant PowerShell snap-ins.

See about_Admin_Filtering for information about advanced filtering options.

## Related Commands
  * [New-AdminScope](New-AdminScope.html)
  * [Set-AdminScope](Set-AdminScope.html)
  * [Rename-AdminScope](Rename-AdminScope.html)
  * [Remove-AdminScope](Remove-AdminScope.html)
  * [Set-AdminScopeMetadata](Set-AdminScopeMetadata.html)
  * [Remove-AdminScopeMetadata](Remove-AdminScopeMetadata.html)
## Parameters

| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| Name | Gets scopes with the specified name. | false | true (ByValue, ByPropertyName) |  |
| Id | Gets the scope with the specified identifier. | false | true (ByPropertyName) |  |
| BuiltIn | Gets scopes with the specified value of the BuiltIn flag. | false | false |  |
| Description | Gets scopes with the specified description. | false | false |  |
| Metadata | Gets records with matching metadata entries.<br>The value being compared with is a concatenation of the key name, a colon, and the value. For example: -Metadata "abc:x*" matches records with a metadata entry having a key name of "abc" and a value starting with the letter "x". | false | false |  |
| Property | Specifies the properties to be returned. This is similar to piping the output of the command through Select-Object, but the properties are filtered more efficiently at the server. | false | false |  |
| ReturnTotalRecordCount | When specified, the cmdlet outputs an error record containing the number of records available. This error record is additional information and does not affect the objects written to the output pipeline. See about_Admin_Filtering for details. | false | false | False |
| MaxRecordCount | Specifies the maximum number of records to return. | false | false | 250 |
| Skip | Skips the specified number of records before returning results. Also reduces the count returned by -ReturnTotalRecordCount. | false | false | 0 |
| SortBy | Sorts the results by the specified list of properties. The list is a set of property names separated by commas, semi-colons, or spaces. Optionally, prefix each name with a + or - to indicate ascending or descending order. Ascending order is assumed if no prefix is present. | false | false | The default sort order is by name or unique identifier. |
| Filter | Gets records that match a PowerShell-style filter expression. See about_Admin_Filtering for details. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller the PowerShell snap-in will connect to. You can provide this as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type
### None
   You cannot pipe input into this cmdlet.
## Return Values
### Citrix.DelegatedAdmin.Sdk.Scope
   Get-AdminScope returns an object for each matching scope.
## Examples

### EXAMPLE 1
```
C:\PS> Get-AdminScope -Name *Sales*
```
   Description<br>-----------<br>List all scopes that contain the word 'Sales'.
### EXAMPLE 2
```
C:\PS> Get-AdminScope -Id 21862daf-e529-4553-ba6e-f7543217111e
```
   Description<br>-----------<br>Gets the details of the scope with the specific id.
