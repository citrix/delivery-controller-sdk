
# Get-Ctxappvserver
Returns URLs for App-V Publishing and Management Servers contained in a Citrix App-V policy. Returned values are in string format.
## Syntax
```
Get-CtxAppVServer -ByteArray <byte[]> [-ConsumedByStudio <bool>] [<CommonParameters>]
```
## Detailed Description
Returns URLs for App-V Publishing and Management Servers contained in a Citrix App-V policy. Returned values are in string format.


## Related Commands

## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| ByteArray | Specifies the Citrix App-V policy created using the New-CtxAppVServer cmdlet. | true | true (ByValue, ByPropertyName) |  |
| ConsumedByStudio | If set to "true", outputs URLs for the App-V Publishing and Management Servers. If set to "false", outputs both the URL and settings for the App-V Publishing Server. | false | false |  |

## Input Type

### 

## Return Values

### String

## Examples

### Example 1
```
$config = Get-BrokerMachineConfiguration -Name appv\*

Get-CtxAppVServer -ByteArray $config[0].Policy
```
#### Description
Returns Publishing Server URL , Management Server URL configured in given policy
