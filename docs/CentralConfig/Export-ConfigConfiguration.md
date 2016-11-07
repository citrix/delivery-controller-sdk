# Export-ConfigConfiguration

   Obtains an XML document containing the configuration of the Site

## Syntax
```
Export-ConfigConfiguration [-ExistingConfigLastChangeTime <String>] [-AdminAddress <String>] [<CommonParameters>]
```

## Detailed Description
   

## Related Commands
## Parameters

| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| ExistingConfigLastChangeTime | The value of ConfigLastChangeTime in the site object of any configuration already held by the caller. If nothing has changed, an empty configuration will be returned with the "Updated" attribute set to false. | false | false | $null |
| AdminAddress | Specifies the address of a XenDesktop controller the PowerShell snap-in will connect to. You can provide this as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type
### This cmdlet does not accept input
   
## Return Values
### string
   The XML document
