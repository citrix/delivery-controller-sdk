
# Get-Userprofilemanagerserviceaddedcapability
Lists the properties that can be configured through user profile configuration.
## Syntax
```
Get-UserProfileManagerServiceAddedCapability [<CommonParameters>]
```
## Detailed Description
This command produces an array containing the names of the properties that can be configured as part of a user profile configuration. Any name that occurs in the array can be used as a parameter for the Set-UserProfileDefinition cmdlet.


## Related Commands

* [New-UserProfileConfiguration](./New-UserProfileConfiguration/)
* [Set-UserProfileDefinition](./Set-UserProfileDefinition/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |

## Input Type

### None
You cannot pipe input to this command
## Return Values

### Object\[\]
The names of the properties that can be configured through user profile configurations
## Examples

### Example 1
```
$properties = Get-UserProfileManagerServiceAddedCapability
```
#### Description
This command creates a list of all the properties that can be set through Set-UserProfileDefinition and stores them in \$properties.
