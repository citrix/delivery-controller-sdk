# Get-ConfigLocalData

   Gets the service local data.

## Syntax
```
Get-ConfigLocalData [-AdminAddress <String>] [<CommonParameters>]
```

## Detailed Description
   Get-ConfigLocalData returns service-and-controller-specific local data. This information is not site-wide, but rather controller-specific. The Configuration Service currently stores the controller product version as local data. The overall site version used by Studio is an aggregate of the product versions from each controller.

## Related Commands
## Parameters

| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| AdminAddress | Specifies the address of a XenDesktop controller the PowerShell snap-in will connect to. You can provide this as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type
### 
   This cmdlet does not accept pipeline input
## Return Values
### Citrix.Configuration.DataModel.LocalData
   Contains the ControllerProductVersion field
## Examples

### EXAMPLE 1
```
C:\PS> Get-ConfigLocalData

ControllerProductVersion
-----------
7.1
```
   Description<br>-----------<br>Gets the service local data.
