# Remove-ProvSchemeScope

   Remove the specified ProvisioningScheme(s) from the given scope(s).

## Syntax
```
Remove-ProvSchemeScope [-Scope] <String[]> -InputObject <ProvisioningScheme[]> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]

Remove-ProvSchemeScope [-Scope] <String[]> -ProvisioningSchemeUid <Guid[]> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]

Remove-ProvSchemeScope [-Scope] <String[]> -ProvisioningSchemeName <String[]> [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
```

## Detailed Description
   The Remove-ProvSchemeScope command is used to remove one or more ProvisioningScheme objects from the given scope(s).

There are multiple parameter sets for this cmdlet, allowing you to identify the ProvisioningScheme objects in different ways: 
 - ProvisioningScheme objects can be piped in or specified by the InputObject parameter 
 - The ProvisioningSchemeUid parameter specifies objects by ProvisioningSchemeUid 
 - The ProvisioningSchemeName parameter specifies objects by ProvisioningSchemeName (supports wildcards)

To remove a ProvisioningScheme from a scope you need permission to change the scopes of the ProvisioningScheme.

If the ProvisioningScheme is not in a specified scope, that scope will be silently ignored.

## Related Commands
  * [Add-ProvSchemeScope](Add-ProvSchemeScope/)
  * [Get-ProvScopedObject](Get-ProvScopedObject/)
## Parameters

| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| Scope | Specifies the scopes to remove the objects from. | true | false |  |
| InputObject | Specifies the ProvisioningScheme objects to be removed. | true | true (ByValue, ByPropertyName) |  |
| ProvisioningSchemeUid | Specifies the ProvisioningScheme objects to be removed by ProvisioningSchemeUid. | true | true (ByValue, ByPropertyName) |  |
| ProvisioningSchemeName | Specifies the ProvisioningScheme objects to be removed by ProvisioningSchemeName. | true | true (ByValue, ByPropertyName) |  |
| LoggingId | Specifies the identifier of the high-level operation this cmdlet call forms a part of. Citrix Studio and Director typically create high-level operations. PowerShell scripts can also wrap a series of cmdlet calls in a high-level operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller the PowerShell snap-in will connect to. You can provide this as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type
### 
   
## Return Values
### None
   ## Notes
   If the command fails, the following errors can be returned.<br>    Error Codes<br>    -----------<br>    UnknownObject<br>        One of the specified objects was not found.<br>    ScopeNotFound<br>        One of the specified scopes was not found.<br>    DatabaseError<br>        An error occurred in the service while attempting a database operation.<br>    DatabaseNotConfigured<br>        The operation could not be completed because the database for the service is not configured.<br>    DataStoreException<br>        An error occurred in the service while attempting a database operation - communication with the database failed for various reasons.<br>    PermissionDenied<br>        You do not have permission to execute this command with the specified objects or scopes.<br>    AuthorizationError<br>        There was a problem communicating with the Citrix Delegated Administration Service.<br>    ConfigurationLoggingError<br>        The operation could not be performed because of a configuration logging error.<br>    CommunicationError<br>        There was a problem communicating with the remote service.<br>    ExceptionThrown<br>        An unexpected error occurred.  For more details, see the Windows event logs on the controller or the XenDesktop logs.
## Examples

### EXAMPLE 1
```
c:\PS>Remove-ProvSchemeScope Finance -ProvisioningSchemeUid 6702C5D0-C073-4080-A0EE-EC74CB537C52
```
   Description<br>-----------<br>Removes a single ProvisioningScheme from the 'Finance' scope.
### EXAMPLE 2
```
c:\PS>Remove-ProvSchemeScope Finance,Marketing -ProvisioningSchemeUid 6702C5D0-C073-4080-A0EE-EC74CB537C52
```
   Description<br>-----------<br>Removes a single ProvisioningScheme from multiple scopes.
### EXAMPLE 3
```
c:\PS>Get-ProvScheme | Remove-ProvSchemeScope Finance
```
   Description<br>-----------<br>Removes all visible ProvisioningScheme objects from the 'Finance' scope.
### EXAMPLE 4
```
c:\PS>Remove-ProvSchemeScope Finance -ProvisioningSchemeName A*
```
   Description<br>-----------<br>Removes ProvisioningScheme objects with a name starting with an 'A' from the 'Finance' scope.
