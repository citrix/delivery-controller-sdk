
# Test-Ctxappvserver
Tests the given URL for the presence of App-V Management and Publishing servers.
## Syntax
```
Test-CtxAppVServer [-AppVManagementServer] <string> [<CommonParameters>]

Test-CtxAppVServer [-AppVPublishingServer] <string> [<CommonParameters>]
```
## Detailed Description
Tests the given URL for the presence of App-V Management and Publishing Servers.


## Related Commands

## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| AppVManagementServer | Machine name of the App-V Management Server. | true | true (ByValue) |  |
| AppVPublishingServer | The URL (including the port number) of the App-V Publishing Server. | false | false |  |

## Input Type

### 

## Return Values

### Boolean

## Examples

### Example 1
```
Test-CtxAppVServer -AppVManagementServer “appv-mansrv”
```
#### Description
Tests whether "appv-mansrv" is a Management Server or not. The name can, but does not need to be specified as a Fully Qualified Domain Name (FQDN). No port number is required.
### Example 2
```
Test-CtxAppVServer -AppVPublishingServer “http://appv-pubsrv.mydomanin.com:8082”
```
#### Description
Tests whether “http://appv-pubsrv.mydomanin.com:8082” is a Publishing Server or not. Specify the full URL address, including FQDN and port number, of the Publishing Server.
