# Get-ConfigServiceGroup

   Gets the service groups that match the parameters supplied.

## Syntax
```
Get-ConfigServiceGroup [-ServiceGroupUid <Guid>] [-ServiceGroupName <String>] [-ServiceType <String>] [-Metadata <String>] [-Property <String[]>] [-ReturnTotalRecordCount] [-MaxRecordCount <Int32>] [-Skip <Int32>] [-SortBy <String>] [-Filter <String>] [-BearerToken <String>] [-AdminAddress <String>] [<CommonParameters>]
```

## Detailed Description
   Use this cmdlet to retrieve existing service groups that match the parameters supplied.  If no parameters are supplied, all the service groups are returned.

## Related Commands
## Parameters

| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| ServiceGroupUid | The unique identifier for the service group. | false | false |  |
| ServiceGroupName |  | false | false |  |
| ServiceType | The service type for the service group. | false | false |  |
| Metadata | Gets records with matching metadata entries.<br>The value being compared with is a concatenation of the key name, a colon, and the value. For example: -Metadata "abc:x*" matches records with a metadata entry having a key name of "abc" and a value starting with the letter "x". | false | false |  |
| Property | Specifies the properties to be returned. This is similar to piping the output of the command through Select-Object, but the properties are filtered more efficiently at the server. | false | false |  |
| ReturnTotalRecordCount | See about_Config_Filtering for details. | false | false | false |
| MaxRecordCount | See about_Config_Filtering for details. | false | false | 250 |
| Skip | See about_Config_Filtering for details. | false | false | 0 |
| SortBy | See about_Config_Filtering for details. | false | false |  |
| Filter | See about_Config_Filtering for details. | false | false |  |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snap-in connects to.  You can provide this as a host name or an IP address. | false | false | LocalHost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type
### 
   
## Return Values
### Citrix.Configuration.Sdk.ServiceGroup<br>    This represents a service instance and has the following parameters;<br>    ServiceGroupUid <Guid><br>        The unique identifier for the service group.<br>    ServiceGroupName <string><br>        The name of the service group.<br>    ServiceType <string><br>        The type of the service group.<br>    Metadata <Citrix.Configuration.Sdk.Metadata[]><br>        The metadata for the service group.
   ## Notes
   In the case of failure, the following errors can result.<br>    Error Codes -----------<br>    DatabaseNotConfigured The operation could not be completed because the database for the service is not configured. PartialData Only a subset of the available data was returned. CouldNotQuueryDatabase The Query required to get the database was not defined. CommunicationError An error occurred while communicating with the service. InvalidFilter A filtering expression was supplied that could not be interpreted for this cmdlet. ExceptionThrown An unexpected error occurred.  To locate more details, see the Windows event logs on the controller being used or examine the XenDesktop logs.
## Examples

### EXAMPLE 1
```
C:\>Get-ConfigServiceGroup
```
   Description<br>-----------<br>Return all the service groups that are registered in the Configuration Service.
### EXAMPLE 2
```
C:\>Get-ConfigRegisteredServiceInstance -ServiceType "config"
```
   Description<br>-----------<br>Return all the service groups that are registered in the Configuration Service and are of type 'config' (i.e. the service groups for the Configuration Service).
