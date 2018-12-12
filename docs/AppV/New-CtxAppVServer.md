
# New-Ctxappvserver
Creates a new Citrix App-V policy containing the specified App-V Management and Publishing Server URLs.
## Syntax
```
New-CtxAppVServer -ManagementServer <String> -PublishingServer <string> [-UserRefreshEnabled <Boolean>] [-UserRefreshOnLogon <Boolean>] [-UserRefreshInterval <int>] [-UserRefreshIntervalUnit <Enum>] [-GlobalRefreshEnabled <Boolean>] [-GlobalRefreshOnLogon <Boolean>] [-GlobalRefreshInterval <Int>] [-GlobalRefreshIntervalUnit <Enum>] [<CommonParameters>]
```
## Detailed Description
Creates a new Citrix App-V policy containing the specified App-V Management and Publishing Server URLs. Additionally, accepts Publishing Server settings that control how and when automatic refresh occurs on the VDA.


## Related Commands

## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| ManagementServer | The URL of the Management Server to add to the Citrix policy. | true | true (ByValue, ByPropertyName) |  |
| PublishingServer | The URL (including the port number) of the Publishing Server to add to the Citrix policy. | true | true (ByValue, ByPropertyName) |  |
| UserRefreshEnabled | Enables a refresh of packages published to user groups either at user logon or at a specified interval. For more information, see the App-V 5.0 documentation at http://technet.microsoft.com/en-us/library/jj687745.aspx | false | false |  |
| UserRefreshOnLogon | Specifies whether or not to initiate a refresh of packages published to user groups on every user logon. For more information, see the App-V 5.0 documentation at http://technet.microsoft.com/en-us/library/jj687745.aspx | false | false |  |
| UserRefreshInterval | Specifies the frequency at which to initiate a refresh of packages published to user groups. This can be either days or hours, as specified by the UserRefreshIntervalUnit setting. For more information, see the App-V 5.0 documentation at http://technet.microsoft.com/en-us/library/jj687745.aspx | false | false |  |
| UserRefreshInterval | Specifies the frequency at which to initiate a refresh of packages published to user groups. This can be either days or hours, as specified by the UserRefreshIntervalUnit setting. For more information, see the App-V 5.0 documentation at http://technet.microsoft.com/en-us/library/jj687745.aspx | false | false |  |
| UserRefreshIntervalUnit | Specifies the unit for the UserRefreshInterval setting. This can be set to either Hours (0) or Days (1). For more information, see the App-V 5.0 documentation at http://technet.microsoft.com/en-us/library/jj687745.aspx | false | false |  |
| GlobalRefreshEnabled | Enables a refresh of packages published to machine groups either at user logon or at a specified interval. For more information, see the App-V 5.0 documentation at http://technet.microsoft.com/en-us/library/jj687745.aspx | false | false |  |
| GlobalRefreshOnLogon | Specifies whether or not to initiate a refresh of packages published to machine groups on every user logon. For more information, see the App-V 5.0 documentation at http://technet.microsoft.com/en-us/library/jj687745.aspx | false | false |  |
| GlobalRefreshInterval | Specifies the frequency at which to initiate a refresh of packages published to machine groups. This can be either days or hours, as specified by the GlobalRefreshIntervalUnit setting. Please refer to App-V 5.0 documentation for details. http://technet.microsoft.com/en-us/library/jj687745.aspx | false | false |  |
| GlobalRefreshIntervalUnit | Specifies the unit for the GlobalRefreshInterval setting. This can be set to either Hours (0) or Days (1). Please refer to App-V 5.0 documentation for details. http://technet.microsoft.com/en-us/library/jj687745.aspx | false | false |  |

## Input Type

### 

## Return Values

### 

## Examples

### Example 1
```
New-CtxAppVServer -ManagementServer http://appv-mansrv.mydomain.com -PublishingServer http://appv-pubsrv.mydomain.com:8082
```
#### Description
Creates a new Citrix Policy for Management Server appv-mansrv  &amp; Publishing Server: appv-pubsrv on port 8082.&lt;br&gt;Default Publishing Server setting is used for http://appv-pubsrv.mydomain.com:8082&lt;br&gt;Default values for Publishing Server settings are:&lt;br&gt;GlobalRefreshEnabled = false&lt;br&gt;GlobalFreshOnLogon = false&lt;br&gt;GlobalIntervalRefreshInterval = 0&lt;br&gt;GlobalRefreshIntervalUnit = Day&lt;br&gt;UserRefreshEnabled = true&lt;br&gt;UserRefreshOnLogon = true&lt;br&gt;UserIntervalRefreshInterval = 0&lt;br&gt;lobalRefreshIntervalUnit = Day
### Example 2
```
New-CtxAppVServer -ManagementServer http://appv-mansrv.mydomain.com -PublishingServer http://appv-pubsrv.mydomaain.com:8082 -GlobalRefreshEnabled $true -GlobalRefreshOnLogon $true -GlobalRefreshInterval 2 -GlobalRefreshIntervalUnit Hour -UserRefreshEnabled $true -UserRefreshOnLogon $true -UserRefreshInterval 3 -UserRefreshIntervalUnit Hour
```
#### Description
Creates a new Citrix Policy for Management Server AppV-Mgmt-Server:8080  &amp; Publishing Server: AppV-Mgmt-Server:8082. User specified Publishing Server settings are used for AppV-Mgmt-Server:8082&lt;br&gt;Following values are used to configure Publishing Server appv-pubsrv&lt;br&gt;GlobalRefreshEnabled = True&lt;br&gt;GlobalRefreshOnLogon = True&lt;br&gt;GlobalIntervalRefreshInterval = 2&lt;br&gt;GlobalRefreshIntervalUnit = Hour&lt;br&gt;UserRefreshEnabled = true&lt;br&gt;UserRefreshOnLogon = true&lt;br&gt;UserIntervalRefreshInterval = 3&lt;br&gt;GlobalRefreshIntervalUnit = Hour
