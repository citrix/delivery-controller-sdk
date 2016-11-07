# New-BrokerConfigurationSlot

   Creates a new configuration slot.

## Syntax
```
New-BrokerConfigurationSlot [-Name] <String> -SettingsGroup <String> [-Description <String>] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
```

## Detailed Description
   Creates a new configuration slot. The SettingsGroup of the slot determines the particular collection of related settings that may be specified in a machine configuration associated with this slot.

For example, the configuration slot may be restricted to configuring Citrix User Profile Manager settings by specifying the SettingsGroup parameter as "G=UPM".

## Related Commands
  * [Get-BrokerConfigurationSlot](Get-BrokerConfigurationSlot.html)
  * [Remove-BrokerConfigurationSlot](Remove-BrokerConfigurationSlot.html)
  * [New-BrokerMachineConfiguration](New-BrokerMachineConfiguration.html)
## Parameters

| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| Name | Name of the new configuration slot. This must be alphanumeric and not contain white space. | true | true (ByPropertyName) |  |
| SettingsGroup | The settings group determines the particular collection of related settings that may be controlled by this slot. This must match the format of a Citrix Group Policy configuration group (e.g. "G=UPM"). Only settings that have this exact group may be specified in a machine configuration associated with this configuration slot. | true | true (ByPropertyName) |  |
| Description | Description of configuration slot. | false | true (ByPropertyName) |  |
| LoggingId | Specifies the identifier of the high level operation that this cmdlet call forms a part of. Desktop Studio and Desktop Director typically create High Level Operations. PowerShell scripts can also wrap a series of cmdlet calls in a High Level Operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |

## Input Type
### None
   You cannot pipe input into this cmdlet.
## Return Values
### Citrix.Broker.Admin.SDK.ConfigurationSlot
   New-BrokerConfigurationSlot returns an object representing the newly created configuration slot
## Examples

### EXAMPLE 1
```
New-BrokerConfigurationSlot -Name "UPM" -SettingsGroup "G=UPM"
```
   Description<br>-----------<br>Create a new slot named "UPM" to configure settings specific to "User Profile Management"
