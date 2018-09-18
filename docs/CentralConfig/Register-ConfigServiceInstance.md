# Register-ConfigServiceInstance

   Allows the registration of a service instance.

## Syntax
```
Register-ConfigServiceInstance -ServiceGroupUid <Guid> -ServiceGroupName <String> -ServiceType <String> -Address <String> -Binding <String> -Version <Int32> -ServiceAccount <String> -InterfaceType <String> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]

Register-ConfigServiceInstance -ServiceGroupUid <Guid> -ServiceGroupName <String> -ServiceType <String> -Address <String> -Binding <String> -Version <Int32> -ServiceAccountSid <String> -InterfaceType <String> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]

Register-ConfigServiceInstance -ServiceInstance <ServiceInstance[]> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
```

## Detailed Description
   Use this cmdlet to register service instance items in the Configuration Service. Service instances can be registered either by retrieving the data directly from other services or by manually entering the details into this command.

If the service group specified by the service instance already exists, the service is added to the service group, otherwise a new service group is created to hold the service instance.

## Related Commands
  * [Unregister-ConfigRegisteredServiceInstance](Unregister-ConfigRegisteredServiceInstance/)
  * [Add-ConfigRegisteredServiceInstanceMetadata](Add-ConfigRegisteredServiceInstanceMetadata/)
  * [Set-ConfigRegisteredServiceInstanceMetadata](Set-ConfigRegisteredServiceInstanceMetadata/)
  * [Remove-ConfigRegisteredServiceInstanceMetadata](Remove-ConfigRegisteredServiceInstanceMetadata/)
  * [Add-ConfigServiceGroupMetadata](Add-ConfigServiceGroupMetadata/)
  * [Set-ConfigServiceGroupMetadata](Set-ConfigServiceGroupMetadata/)
  * [Remove-ConfigServiceGroupMetadata](Remove-ConfigServiceGroupMetadata/)
## Parameters

| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| ServiceGroupUid | The Service Group Unique Identifier | true | true (ByPropertyName) |  |
| ServiceGroupName | The name of the service group | true | true (ByPropertyName) |  |
| ServiceType | The type of the service group | true | true (ByPropertyName) |  |
| Address | The address that is used to access the service instance. | true | true (ByPropertyName) |  |
| Binding | The binding type that must be used to access the service instance. | true | true (ByPropertyName) |  |
| Version | The version of the service instance. | true | true (ByPropertyName) |  |
| ServiceAccount | The AD computer account name (domain qualified) for the computer on which the service instance is hosted. | true | true (ByPropertyName) |  |
| InterfaceType | The type of interface that the service provides (i.e. SDK, InterService, Peer). | true | true (ByPropertyName) |  |
| ServiceAccountSid | The AD computer account Sid for the computer on which the service instance is hosted. | true | true (ByPropertyName) |  |
| ServiceInstance | The service instances to register. | true | true (ByValue) |  |
| LoggingId | Specifies the logging id of the high-level operation that this cmdlet is part of. | false | true (ByPropertyName) |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snap-in connects to.  You can be provide this as a host name or an IP address. | false | false | LocalHost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type
### Citrix.Configuration.Sdk.ServiceInstance<br>   An object with the following parameters can be used to register a service instance.<br>     Address,<br>     ServiceGroupUid,<br>     ServiceGroupName,<br>     ServiceType,<br>     Binding,<br>     Version,<br>     InterfaceType.
   
## Return Values
### Citrix.Configuration.Sdk.ServiceInstance<br>    This represents a service instance and has the following parameters;<br>    ServiceGroupUid <Guid><br>        The unique identifier for the service group to which the service instance belongs.<br>    ServiceGroupName <string><br>        The name of the service group to which the service instance belongs.<br>    ServiceInstanceUid <Guid><br>        The unique identifier for the service instance.<br>    ServiceType <string><br>        The type of the service group.<br>    Address <string><br>        The contact address for the service instance.<br>    Binding <string><br>        The binding to use for connections to the service instance.<br>    Version <int><br>        The version of the service instance.<br>    ServiceAccount <string><br>        The AD computer account for the computer that is providing the service instance.<br>    ServiceAccountSid <string><br>        The AD computer account SID for the computer that is providing the service instance.<br>    InterfaceType <string><br>        The interface type for the service instance.<br>    Metadata <Citrix.Configuration.Sdk.Metadata[]><br>        The metadata for the service instance.
   ## Notes
   In the case of failure, the following errors can result.<br>    Error Codes ----------- ActiveDirectoryAccountResolutionFailed The account name provided could not be found in Active Directory. ServiceGroupWithSameUidExistsForDifferentServiceGroupNameOrSameUidExistsForDifferentServiceGroupNameOrServiceType The service group name or service type do not match the service group found with the specified uid. TypeAlreadyExists A different service group with the same type is registered already in the Configuration Service. DatabaseError An error occurred in the service while attempting a database operation. DatabaseNotConfigured The operation could not be completed because the database for the service is not configured. DataStoreException An error occurred in the service while attempting a database operation - communication with the database failed for various reasons. CommunicationError An error occurred while communicating with the service. ExceptionThrown An unexpected error occurred.  For more details, see the Windows event logs on the controller being used or examine the XenDesktop logs.
## Examples

### EXAMPLE 1
```
C:\PS>Get-ConfigServiceInstance | Register-ConfigServiceInstance
```
   Description<br>-----------<br>Gets the service instances for the Configuration Service and registers them.
