# Get-AcctIdentityPool

   Gets existing identity pools.

## Syntax
```
Get-AcctIdentityPool [[-IdentityPoolName] <String>] [-IdentityPoolUid <Guid>] [-Lock <Boolean>] [-ScopeId <Guid>] [-ScopeName <String>] [-ReturnTotalRecordCount] [-MaxRecordCount <Int32>] [-Skip <Int32>] [-SortBy <String>] [-Filter <String>] [-AdminAddress <String>] [<CommonParameters>]
```

## Detailed Description
   Provides the ability to locate existing identity pools.

## Related Commands
  * [New-AcctIdentityPool](New-AcctIdentityPool.html)
  * [Remove-AcctIdentityPool](Remove-AcctIdentityPool.html)
  * [Rename-AcctIdentityPool](Rename-AcctIdentityPool.html)
  * [Set-AcctIdentityPool](Set-AcctIdentityPool.html)
## Parameters

| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| IdentityPoolName | The name of the identity pool. | false | false |  |
| IdentityPoolUid | The unique identifier for the identity pool. | false | false |  |
| Lock | Whether the identity pool is locked or not. | false | false |  |
| ScopeId | Gets only results with a scope matching the specified scope identifier. | false | false |  |
| ScopeName | Gets only results with a scope matching the specified scope name. | false | false |  |
| ReturnTotalRecordCount | See about_Acct_Filtering for details. | false | false | false |
| MaxRecordCount | See about_Acct_Filtering for details. | false | false | 250 |
| Skip | See about_Acct_Filtering for details. | false | false | 0 |
| SortBy | See about_Acct_Filtering for details. | false | false |  |
| Filter | See about_Acct_Filtering for details. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snap-in connects to.  You can provide this as a host name or an IP address. | false | false | LocalHost. Once a value is provided by any cmdlet, this value will become the default. |
| ZoneUid | Represents the Zoneid. | false | false |  |

## Input Type
### 
   
## Return Values
### Citrix.ADIdentity.Sdk.IdentityPool<br>    This object provides details of the identity pool and contains the following information:<br>IdentityPoolName <string><br>    The name of the identity pool.<br>IdentityPoolUid <Guid><br>    The unique identifier for the identity pool.<br>NamingScheme <string><br>    The naming scheme for the identity pool.<br>NamingSchemeType <Citrix.XDInterServiceTypes.ADIdentityNamingScheme><br>    The naming scheme type for the identity pool. This can be one of the following:<br>        Numeric - naming scheme uses numeric indexes<br>        Alphabetic - naming scheme uses alphabetic indexes<br>StartCount <int><br>    The next index to be used when creating an identity from the identity pool.<br>OU <string><br>    The Active Directory distinguished name for the OU in which accounts created from this identity pool will be created.<br>Domain <string><br>    The Active Directory domain that accounts in the pool belong to.<br>Lock <Boolean><br>    Indicates if the identity pool is locked.
   ## Notes
   In the case of failure, the following errors can result.<br>    Error Codes<br>    -----------<br>    PartialData<br>    Only a subset of the available data was returned.<br>    CouldNotQueryDatabase<br>    The query required to get the database was not defined.<br>    PermissionDenied<br>    The user does not have administrative rights to perform this operation.<br>    ConfigurationLoggingError<br>    The operation could not be performed because of a configuration logging error<br>    CommunicationError<br>    An error occurred while communicating with the service.<br>    DatabaseNotConfigured<br>    The operation could not be completed because the database for the service is not configured.<br>    InvalidFilter<br>    A filtering expression was supplied that could not be interpreted for this cmdlet.<br>    ExceptionThrown<br>    An unexpected error occurred.  To locate more details, see the Windows event logs on the controller being used or examine the XenDesktop logs.
## Examples

### EXAMPLE 1
```
C:\PS>Get-AcctIdentityPool

IdentityPoolName : MyPool
IdentityPoolUid  : 22072d9e-6a8f-494b-a5bc-2ef18ca4b915
NamingScheme     : Acc####
NamingSchemeType : Numeric
StartCount       : 1
OU               :
Domain           : mydomain.com
Lock             : True

IdentityPoolName : MyPool2
IdentityPoolUid  : 03743136-e43b-4a87-af74-ab71686b3c16
NamingScheme     : Test####
NamingSchemeType : Alphabetic
StartCount       : 1
OU               :
Domain           : mydomain.com
Lock             : False
```
   Description<br>-----------<br>Gets all the identity pools.
### EXAMPLE 2
```
C:\PS>Get-AcctIdentityPool -IdentityPoolName M*

IdentityPoolName : MyPool
IdentityPoolUid  : 22072d9e-6a8f-494b-a5bc-2ef18ca4b915
NamingScheme     : Acc####
NamingSchemeType : Numeric
StartCount       : 1
OU               :
Domain           : mydomain.com
Lock             : True
```
   Description<br>-----------<br>Gets all the identity pools beginning with the character 'M'.
