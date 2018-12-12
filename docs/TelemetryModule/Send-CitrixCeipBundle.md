
# Send-Citrixceipbundle
Sends the previously saved Ceip upload to CIS(Citrix Insights Service).
## Syntax
```
Send-CitrixCeipBundle -Path <String> [<CommonParameters>]
```
## Detailed Description
This cmdlet sends the previously saved Ceip upoad to CIS(Citrix Insights Service).


## Related Commands

* [Start-CitrixCeipUpload](./Start-CitrixCeipUpload/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| Path | Path to previously saved bundle. | true | true |  |

## Input Type

### 

## Return Values

### 

## Examples

### Example 1: Send Previously Saved Bundle
```
PS C:\>Send-CitrixCeipBundle -Path C:\saved-bundle.zip
```If you saved a bundle via Start-CitrixCeipUpload, you can send it to CIS(Citrix Insights Service) using this command.
