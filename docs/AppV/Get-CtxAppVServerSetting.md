
# Get-Ctxappvserversetting
Returns settings for the specified App-V Publishing Server.
## Syntax
```
Get-CtxAppVServerSetting -AppVPublishingServer <string> [<CommonParameters>]
```
## Detailed Description
Returns settings for the specified App-V Publishing Server. For more information about these settings, see the App-V documentation on the Microsoft website at http://technet.microsoft.com/en-us/library/jj687745.aspx


## Related Commands

## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| AppVPublishingServer | The full URL (including port number) of the Publishing Server for which settings are to be returned. | true | true (ByValue, ByPropertyName) |  |

## Input Type

### 

## Return Values

### Publishing Server Settings. These Settings Are:
GlobalRefreshEnabled<br>GlobalRefreshOnLogon<br>GlobalRefreshInterval<br>GlobalRefreshIntervalUnit<br>UserRefreshEnabled<br>UserRefreshOnLogon<br>UserRefreshInterval<br>UserRefreshIntervalUnit
## Examples

### Example 1
```
Get-CtxAppVServerSetting -AppVPublishingServer http://appv-pubsrv.mydomain.com:8082
```
#### Description
This example returns settings associated with http://appv-pubsrv.mydomain.com:8082 in the following format:&lt;br&gt;GlobalRefreshEnabled: false&lt;br&gt;GlobalRefreshOnLogon: false&lt;br&gt;GlobalRefreshInterval: 0&lt;br&gt;GlobalRefreshIntervalUnit: Day&lt;br&gt;UserRefreshEnabled: true&lt;br&gt;UserRefreshOnLogon: false&lt;br&gt;UserRefreshInterval: 0&lt;br&gt;UserRefreshIntervalUnit: Hour
