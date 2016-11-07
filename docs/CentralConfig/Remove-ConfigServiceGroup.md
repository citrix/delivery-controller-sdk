# Remove-ConfigServiceGroup

   Removes service groups.

## Syntax
```
Remove-ConfigServiceGroup [-ServiceGroupUid] <Guid> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
```

## Detailed Description
   Use this cmdlet to remove a service group and all the service instances that it contains.

## Related Commands
  * [Register-ConfigServiceInstance](Register-ConfigServiceInstance.html)
  * [Add-ConfigServiceGroupMetadata](Add-ConfigServiceGroupMetadata.html)
  * [Set-ConfigServiceGroupMetadata](Set-ConfigServiceGroupMetadata.html)
  * [Remove-ConfigServiceGroupMetadata](Remove-ConfigServiceGroupMetadata.html)
## Parameters

| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| ServiceGroupUid | The unique identifier for the service group. | true | true (ByPropertyName) |  |
| LoggingId | Specifies the logging id of the high-level operation this cmdlet invocation is part of. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snap-in connects to.  You can provide this as a host name or an IP address. | false | false | LocalHost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type
### 
   
## Return Values
### 
   ## Notes
   In the case of failure, the following errors can result.<br>    Error Codes ----------- ServiceGroupObjectNotFound The service group specified could not be located. DatabaseError An error occurred in the service while attempting a database operation. DatabaseNotConfigured The operation could not be completed because the database for the service is not configured. DataStoreException An error occurred in the service while attempting a database operation - communication with the database failed for various reasons. CommunicationError An error occurred while communicating with the service. ExceptionThrown An unexpected error occurred.  For more details, see the Windows event logs on the controller being used or examine the XenDesktop logs.
## Examples

### EXAMPLE 1
```
C:\PS>Remove-ConfigServiceGroup -ServiceGroupUid 31951f6f-7703-4abb-938a-2861d76ecfea
```
   Description<br>-----------<br>Removes the service group (and all contained service instances) for the service group with a unique identifier of '31951f6f-7703-4abb-938a-2861d76ecfea'.
### EXAMPLE 2
```
C:\PS> Get-ConfigServiceGroup | Remove-ConfigServiceGroup
```
   Description<br>-----------<br>Removes all the service groups (and all contained service instances) for the XenDesktop deployment.
