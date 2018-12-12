# Set-ConfigRegisteredServiceInstance

   Updates a service instance.

## Syntax
```
Set-ConfigRegisteredServiceInstance -ServiceInstanceUid <Guid> -Address <String> [-PassThru] [-LoggingId <Guid>] [-BearerToken <String>] [-AdminAddress <String>] [<CommonParameters>]
```

## Detailed Description
   Use this cmdlet to change the address property of an existing service instance that is registered in the Configuration Service.

## Related Commands
  * [Get-ConfigRegisteredServiceInstance](Get-ConfigRegisteredServiceInstance.html)
  * [Register-ConfigServiceInstance](Register-ConfigServiceInstance.html)
  * [Unregister-ConfigRegisteredServiceInstance](Unregister-ConfigRegisteredServiceInstance.html)
## Parameters

| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| ServiceInstanceUid | The unique identifier for the service instance to be updated. | true | true (ByPropertyName) |  |
| Address | The new address for the service instance. | true | false |  |
| PassThru | Defines whether or not the command returns a result showing the new state of the updated service instance. | false | false | true |
| LoggingId | Specifies the logging id of the high-level operation this cmdlet invocation is part of. | false | false |  |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snap-in connects to.  You can provide this as a host name or an IP address. | false | false | LocalHost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type
### 
   
## Return Values
### Citrix.Configuration.Sdk.ServiceInstance<br>    This represents a service instance and has the following parameters:<br>    ServiceGroupUid <Guid><br>        The unique identifier for the service group to which the service instance belongs.<br>    ServiceGroupName <string><br>        The name of the service group to which the service instance belongs.<br>    ServiceInstanceUid <Guid><br>        The unique identifier for the service instance.<br>    ServiceType <string><br>        The type of the service group.<br>    Address <string><br>        The contact address for the service instance.<br>    Binding <string><br>        The binding to use for connections to the service instance.<br>    Version <int><br>        The version of the service instance.<br>    ServiceAccount <string><br>        The AD computer account for the computer that is providing the service instance.<br>    ServiceAccountSid <string><br>        The AD computer account SID for the computer that is providing the service instance.<br>    InterfaceType <string><br>        The interface type for the service instance.<br>    Metadata <Citrix.Configuration.Sdk.Metadata[]><br>        The metadata for the service instance.
   ## Notes
   In the case of failure, the following errors can result.<br>    Error Codes ----------- ObjectToUpdateDoesNotExist The service instance specified could not be located. DatabaseError An error occurred in the service while attempting a database operation. DatabaseNotConfigured The operation could not be completed because the database for the service is not configured. DataStoreException An error occurred in the service while attempting a database operation - communication with the database failed for various reasons. CommunicationError An error occurred while communicating with the service. ExceptionThrown An unexpected error occurred.  For more details, see the Windows event logs on the controller being used or examine the XenDesktop logs.
## Examples

### EXAMPLE 1
```
C:\PS>Set-ConfigRegisteredServiceInstance -ServiceInstanceUid "9805f39d-99eb-44f0-8f63-9d8e3f1228e0" -Address "http://myServer.com/Citrix/sdkHostingUnitService"
```
   Description<br>-----------<br>Update the service instance with the unique identifier of '9805f39d-99eb-44f0-8f63-9d8e3f1228e0' to use the new address.
