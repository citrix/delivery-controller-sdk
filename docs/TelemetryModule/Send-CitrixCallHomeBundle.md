
# Send-Citrixcallhomebundle
Sends the previously saved Call Home upload to CIS(Citrix Insights Service).
## Syntax
```
Send-CitrixCallHomeBundle -Credential <PSCredential> -Path <String> [<CommonParameters>]

Send-CitrixCallHomeBundle -UploadGrantToken <String> -Path <String> [<CommonParameters>]

Send-CitrixCallHomeBundle -UploadToken <String> -Path <String> [<CommonParameters>]
```
## Detailed Description
This cmdlet sends the previously saved Call Home upoad to CIS(Citrix Insights Service).


## Related Commands

* [Enable-CitrixCallHome](./Enable-CitrixCallHome/)
* [Get-CitrixCallHome](./Get-CitrixCallHome/)
* [Set-CitrixCallHomeSchedule](./Set-CitrixCallHomeSchedule/)
* [Get-CitrixCallHomeSchedule](./Get-CitrixCallHomeSchedule/)
* [Start-CitrixCallHomeUpload](./Start-CitrixCallHomeUpload/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| Credential | MyCitrix Credential | true | true |  |
| UploadGrantToken | Upload Grant Token | true | true |  |
| UploadToken | Upload Token | true | true |  |
| Path | Path to previously saved bundle. | true | true |  |

## Input Type

### 

## Return Values

### 

## Examples

### Example 1: Send Previously Saved Bundle
```
PS C:\>Send-CitrixCallHomeBundle -Credential (Get-Credential) -Path C:\saved-bundle.zip
```If you saved a bundle via Start-CitrixCallHomeUpload, you can send it to CIS(Citrix Insights Service) using this command.
