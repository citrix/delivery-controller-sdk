﻿
# Get-Provobjectreference
Returns the number of local objects holding references to objects from other services.
## Syntax
```
Get-ProvObjectReference [-HostingUnitUid <Guid[]>] [-IdentityPoolUid <Guid[]>] [-BearerToken <String>] [-AdminAddress <String>] [<CommonParameters>]
```
## Detailed Description
Returns for each hosting unit or identity pool GUID the number of references by provisioning schemes or by long running task. This check is done without regard for scoping of existing provisioning schemes, references by inaccessible schemes are also checked.


## Related Commands

## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| HostingUnitUid | The identifiers of the hosting units(s) to be tested. | false | true (ByPropertyName) |  |
| IdentityPoolUid | The identifiers of the identity pool(s) to be tested. | false | true (ByPropertyName) |  |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller the PowerShell snap-in will connect to. You can provide this as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type

### 

## Return Values

### Objectreferencecount
An object which contain the input object identifier, its type, the type of referencing object and the number of references.
## Notes
In the case of failure, the following errors can result.<br>    Error Codes<br>    -----------<br>    DatabaseError<br>    An error occurred in the service while attempting a database operation.<br>    DatabaseNotConfigured<br>    The operation could not be completed because the database for the service is not configured.<br>    ServiceStatusInvalidDb<br>    An error occurred in the service while attempting a database operation - communication with the database failed for<br>    for various reasons.<br>    CommunicationError<br>    An error occurred while communicating with the service.<br>    PermissionDenied<br>    The user does not have administrative rights to perform this operation.<br>    ExceptionThrown<br>    An unexpected error occurred.  To locate more details, see the Windows event logs on the controller being used or examine the XenDesktop logs.
## Examples

### Example 1
```
Get-ProvObjectReference -HostingUnitUid 5B66A060-85E1-4DBD-9D1B-BF79881D3BB1

Count         : 1

ObjectId      : 5b66a060-85e1-4dbd-9d1b-bf79881d3bb1

Source        : ProvisioningScheme

Target        : HostingUnit

Count         : 0

ObjectId      : 5b66a060-85e1-4dbd-9d1b-bf79881d3bb1

Source        : Task

Target        : HostingUnit
```
#### Description
This checks a single hosting unit for objects that have references to them; in this case we only have a single provisioning scheme that relates to it.
