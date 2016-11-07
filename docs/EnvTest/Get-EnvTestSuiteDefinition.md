# Get-EnvTestSuiteDefinition

   Gets one or more test suite definitions.

## Syntax
```
Get-EnvTestSuiteDefinition [-TestSuiteId <String[]>] [-CultureName <String>] [-AdminAddress <String>] [<CommonParameters>]
```

## Detailed Description
   Returns a list of test suite definitions that are available from currently running components.

## Related Commands
  * [Get-EnvTestDefinition](Get-EnvTestDefinition.html)
  * [Get-EnvTestTask](Get-EnvTestTask.html)
  * [Start-EnvTestTask](Start-EnvTestTask.html)
  * [Switch-EnvTestTask](Switch-EnvTestTask.html)
  * [Stop-EnvTestTask](Stop-EnvTestTask.html)
  * [Remove-EnvTestTask](Remove-EnvTestTask.html)
  * [Add-EnvTestTaskMetadata](Add-EnvTestTaskMetadata.html)
  * [Remove-EnvTestTaskMetadata](Remove-EnvTestTaskMetadata.html)
## Parameters

| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| TestSuiteId | The id of one or more test suites. | false | true (ByValue) |  |
| CultureName | The culture name in which to produce results. The culture name is in standard language/region-code format; for example "en-US". | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller the PowerShell snap-in will connect to. You can provide this as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type
### System.String
   A test suite id.### System.String[]
   An array of test suite ids.
## Return Values
### Citrix.EnvTest.Sdk.EnvTestSuiteDefinition
   The definition of a test suite
## Examples

### EXAMPLE 1
```
$allTestSuiteDefinitions = Get-EnvTestSuiteDefinition
```
   Description<br>-----------<br>Retrieve all test suites.
### EXAMPLE 2
```
$allTestSuiteDefinitionsTranslatedIntoSpanish = Get-EnvTestSuiteDefinition -CultureName es-ES
```
   Description<br>-----------<br>Retrieve all test suites with localized properties returned in Spanish.
### EXAMPLE 3
```
$infrastructureSuiteDefinition = Get-EnvTestSuiteDefinition -TestSuiteId Infrastructure
```
   Description<br>-----------<br>Retrieve the definition of the 'Infrastructure' test suite.
