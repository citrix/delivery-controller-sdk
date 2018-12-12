
# Test-Citrixcallhomeuploadcredentials
Verifies the status of the Citrix Call Home Upload credentials.
## Syntax
```
Test-CitrixCallHomeUploadCredentials [-Credential] <PSCredential> [-Collect <String>] [<CommonParameters>]
```
## Detailed Description
Returns the status of the Citrix Call Home Upload credentials. Valid Citrix credentials are required. These credentials are not persisted.


## Related Commands

* [Get-Credential](./Get-Credential/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| Credential | Represents the Citrix user account of an authorized administrator. The machine identity within Citrix Insight Services is derived from this user. | true | false |  |
| Listen |  | false | false |  |

## Input Type

### System.Management.Automation.Pscredential
This cmdlet accepts a PSCredential object as input that populates the Credential parameter.
## Return Values

### Status

## Examples

### Example: Verify A Citrix Call Home Upload Credential
```
C:\PS>$cisCredential = Get-Credential

C:\PS>$status = Test-CitrixCallHomeUploadCredentials –Credential $cisCredential
```Returns the status of the Citrix Call Home Upload credentials.
