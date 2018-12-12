
# New-Citrixcallhomeuploadgranttoken
Returns a Citrix Call Home upload grant token that can then be used by Start-CitrixCallHomeUpload to obtain permission to upload to the Citrix Insight Services.
## Syntax
```
New-CitrixCallHomeUploadGrantToken [-Credential] <PSCredential> [-ValidUtil <String>] [<CommonParameters>]
```
## Detailed Description
Returns a Citrix Call Home upload grant token that can then be used by Start-CitrixCallHomeUpload to obtain permission to upload to the Citrix Insight Services. Valid Citrix credentials are required. These credentials are not persisted.


## Related Commands

* [Get-Credential](./Get-Credential/)
* [Start-CitrixCallHomeUpload](./Start-CitrixCallHomeUpload/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| Credential | Represents the Citrix user account of an authorized administrator.  The machine identity within Citrix Insight Services is derived from this user. | true | false |  |
| ValidUtil |  | false | false |  |

## Input Type

### System.Management.Automation.Pscredential
This cmdlet accepts a PSCredential object as input that populates the Credential parameter.
### System.String
This cmdlet accepts a String object as input that populates the ValidUtil parameter.
## Return Values

### Uploadgranttoken

## Examples

### Example 1: Obtain A Citrix Call Home Upload Grant Token That's Valid Until 2017/1/1 00:00:00
```
C:\PS>$cisCredential = Get-Credential

C:\PS>$uploadGrantToken = New-CitrixCallHomeUploadGrantToken –Credential $cisCredential -ValidUntil "2017/1/1 00:00:00"
```Obtains a Citrix Call Home upload grant token from Citrix Insight Services. This may then be passed to Start-CitrixCallHomeUpload to authenticate an upload.
