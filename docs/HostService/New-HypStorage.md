﻿# New-HypStorage

   Creates a new storage tier definition for use in a subsequent New-Item operation.

## Syntax
```
New-HypStorage [-JobGroup] <Guid> -StorageType <StorageType> -StoragePath <String[]> [-AdminAddress <String>] [<CommonParameters>]
```

## Detailed Description
   Use this command to create a new storage tier definition, this definition can then be associated with a subsequent New-Item operation via the JobGroup reference.

## Related Commands
## Parameters

| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| JobGroup | Specifies the JobGroup uid that is used to associate data from calls to this cmdlet with the subsequent New-Item operation. | true | false |  |
| StorageType | The type of the new storage tier. Currently the only storage type is TemporaryStorage. | true | false |  |
| StoragePath | Specifies the path to the storage that will be added. The path must be in one of the following formats: <drive>:\Connections\<ConnectionName>\MyStorage.storage or  <drive>:\Connections\{<Connection Uid>}\MyStorage.storage | true | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller the PowerShell snap-in will connect to. You can provide this as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type
### 
   
## Return Values
### 
   
## Examples

### EXAMPLE 1
```
c:\PS>$job = [Guid]::NewGuid()
c:\PS>New-HypStorage -JobGroup $job -StorageType TemporaryStorage -StoragePath @('XDHyp:\Connections\MyConnection\Primary Storage.storage')
```
   Description<br>-----------<br>The command creates a new job group with the unique id specified by $job which can subsequently be fed into the New-Item cmdlet. It defines a TemporaryStorage tier which will cause disks to be added to the storage path 'XDHyp:\Connections\MyConnection\Primary Storage.storage'.