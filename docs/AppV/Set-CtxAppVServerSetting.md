
# Set-Ctxappvserversetting
Specifies the App-V Publishing Server settings to use on the VDA. These settings determine whether or not the App-V Client can automatically initiate a publishing refresh on certain events such as user logon or at specified intervals.
## Syntax
```
Set-CtxAppVServerSetting -AppVPublishingServer <string> [-UserRefreshEnabled <Boolean>] [-UserRefreshOnLogon <Boolean>] [-UserRefreshInterval <int>] [-UserRefreshIntervalUnit <Enum>] [-GlobalRefreshEnabled <Boolean>] [-GlobalRefreshOnLogon <Boolean>] [-GlobalRefreshInterval <int>] [-GlobalRefreshIntervalUnit <Enum>] [<CommonParameters>]
```
## Detailed Description
Specifies the App-V Publishing Server settings to use on the VDA. These settings determine whether or not the App-V Client can automatically initiate a publishing refresh on certain events such as user logon or at specified intervals. Please refer to Microsoft App-V 5.0 documentation for more details on these settings : http://technet.microsoft.com/en-us/library/jj687745.aspx


## Related Commands

## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| AppVPublishingServer | The full URL (including port number) of the Publishing Server for which settings are to be set. | true | true (ByValue, ByPropertyName) |  |
| UserRefreshEnabled | Enables a refresh of packages published to user groups either at user logon or at a specified interval. For more information, see the App-V documentation on the Microsoft website at http://technet.microsoft.com/en-us/library/jj687745.aspx | True | false |  |
| UserRefreshOnLogon | Specifies whether or not to initiate a refresh of packages published to user groups on every user logon. For more information, see the App-V documentation on the Microsoft website at http://technet.microsoft.com/en-us/library/jj687745.aspx | true | false |  |
| UserRefreshInterval | Specifies the frequency at which to initiate a refresh of packages published to user groups. This can be either days or hours, as specified by the UserRefreshIntervalUnit setting. For more information, see the App-V documentation on the Microsoft website at http://technet.microsoft.com/en-us/library/jj687745.aspx | true | false |  |
| UserRefreshIntervalUnit | Specifies the unit for the UserRefreshInterval setting. This can be set to either Hours (0) or Days (1). For more information, see the App-V documentation on the Microsoft website at http://technet.microsoft.com/en-us/library/jj687745.aspx | true | false |  |
| GlobalRefreshEnabled | Enables a refresh of packages published to machine groups either at user logon or at a specified interval. For more information, see the App-V documentation on the Microsoft website at http://technet.microsoft.com/en-us/library/jj687745.aspx | True | false |  |
| GlobalRefreshOnLogon | Specifies whether or not to initiate a refresh of packages published to machine groups on every user logon. For more information, see the App-V documentation on the Microsoft website at http://technet.microsoft.com/en-us/library/jj687745.aspx | true | false |  |
| GlobalRefreshInterval | Specifies the frequency at which to initiate a refresh of packages published to machine groups. This can be either days or hours, as specified by the GlobalRefreshIntervalUnit setting. For more information, see the App-V documentation on the Microsoft website at http://technet.microsoft.com/en-us/library/jj687745.aspx | true | false |  |
| GlobalRefreshIntervalUnit | Specifies the unit for the GlobalRefreshInterval setting. This can be set to either Hours (0) or Days (1). For more information, see the App-V documentation on the Microsoft website at http://technet.microsoft.com/en-us/library/jj687745.aspx | true | false |  |

## Input Type

### 

## Return Values

### 

## Examples

### Example 1
```
Set-CtxAppVServerSetting -AppVPublishingServer http://appv-pubsrv.mydomain.com:8082 -GlobalRefreshEnabled $true -GlobalRefreshOnLogon $true -GlobalRefreshInterval 2 -GlobalRefreshIntervalUnit Hour -UserRefreshEnabled $true -UserRefreshOnLogon $true -UserRefreshInterval 3 -UserRefreshIntervalUnit Hour
```
