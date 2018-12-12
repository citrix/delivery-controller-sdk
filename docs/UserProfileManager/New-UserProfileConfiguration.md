
# New-Userprofileconfiguration
Creates a new configuration for Citrix Profile Management, with all settings in their default initial state.
## Syntax
```
New-UserProfileConfiguration [<CommonParameters>]
```
## Detailed Description
This command returns a byte array (or "blob"), which can be passed to the Get-UserProfileDefinition and Set-UserProfileDefinition commands to inspect and modify a configuration set.

Use this command to bootstrap the configuration process in the case where no configuration policy objects are available in the Broker's database, or when you wish to create a fresh configuration that is separate from any that already exist.

No settings will be explicitly configured in the new configuration set. The properties of the configuration will be based on documented default values. Use Set-UserProfileDefinition to alter the state of any property within the configuration set.


## Related Commands

## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |

## Input Type

### None

## Return Values

### Byte\[\]
The new configuration set, which can be piped directly into Get-UserProfileDefinition to receive the named properties.
## Examples

### Example 1
```
C:\PS>$blob = New-UserProfileConfiguration

C:\PS>Get-UserProfileDefinition -ByteArray $blob
```
#### Description
The first command creates a fresh configuration set in its default state, and stores it in a Windows PowerShell variable. The second command interprets the new blob, and would output the individual properties of the default configuration.
### Example 2
```
C:\PS>New-UserProfileConfiguration | Get-UserProfileDefinition
```
#### Description
This command creates a fresh configuration set in its default state, and pipes the resulting byte array through to Get-UserProfileDefinition, which will interpret it and output its individual properties.
