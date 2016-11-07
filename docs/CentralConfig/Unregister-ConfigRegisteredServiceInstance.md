# Unregister-ConfigRegisteredServiceInstance

   Removes a service instance from the Configuration Service registry.

## Syntax
```
Unregister-ConfigRegisteredServiceInstance [-ServiceInstanceUid] <Guid> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
```

## Detailed Description
   Use this cmdlet to remove a service instance from the Configuration Service registry. This does not remove any service groups (if all service instances for a Service Group are removed, an empty service group remains and must be removed using the Remove-ConfigServiceGroup command).

## Related Commands
  * [Register-ConfigServiceInstance](Register-ConfigServiceInstance.html)
## Parameters

| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| ServiceInstanceUid | The unique identifier for the service instance to be removed. | true | true (ByPropertyName) |  |
| LoggingId | Specifies the logging id of the high-level operation this cmdlet invocation is part of. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snap-in connects to.  You can provide this as a host name or an IP address. | false | false | LocalHost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type
### Citrix.Configuration.Sdk.ServiceInstance<br>   An object with a parameter called 'ServiceInstanceUid' can be used to unregister service instances.
   
## Return Values
### 
   ## Notes
   In the case of failure, the following errors can result.<br>    Error Codes ----------- ServiceInstanceObjectNotFound The service instance specified could not be located. DatabaseError An error occurred in the service while attempting a database operation. DatabaseNotConfigured The operation could not be completed because the database for the service is not configured. DataStoreException An error occurred in the service while attempting a database operation - communication with the database failed for various reasons. CommunicationError An error occurred while communicating with the service. ExceptionThrown An unexpected error occurred.  For more details, see the Windows event logs on the controller being used or examine the XenDesktop logs.
## Examples

### EXAMPLE 1
```
C:\PS>Get-ConfigRegisteredServiceInstance -ServiceType "Config" | Unregister-ConfigRegisteredServiceInstance
```
   Description<br>-----------<br>Unregisters all the service instances that are for a service type of 'Config' from the Configuration Service instance register.
