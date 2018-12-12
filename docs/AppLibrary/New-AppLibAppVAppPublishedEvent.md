﻿
# New-Applibappvapppublishedevent
Records telemetry information
## Syntax
```
New-AppLibAppVAppPublishedEvent -ApplicationUid <Int32> -ApplicationName <String> -RepositoryTypeValue <Int32> [-LoggingId <Guid>] [-BearerToken <String>] [-AdminAddress <String>] [<CommonParameters>]
```
## Detailed Description
Indicates that an App-V application is published to a delivery group.


## Related Commands

## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| ApplicationUid | The broker application Uid | true | false | None - This is a mandatory parameter |
| ApplicationName | The application name | true | true (ByPropertyName) | None - This is a mandatory parameter |
| RepositoryTypeValue | Indicates the source location of the application | true | false | None - This is a mandatory parameter |
| LoggingId | Specifies the identifier of the high-level operation this cmdlet call forms a part of. Citrix Studio and Director typically create high-level operations. PowerShell scripts can also wrap a series of cmdlet calls in a high-level operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller the PowerShell snap-in will connect to. You can provide this as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type

### 

## Return Values

### 

## Notes
Telemetry information is sent annonymously to CEIP(Customer Experiance Improvement Program) when the user has opted into the service.<br>    Only the information specified in the parameters are sent to CEIP<br>    RepositoryTypeValue(0) = Microsoft App-V Server<br>    RepositoryTypeValue(1) = Citrix AppLibrary
## Examples

### Example 1
```
New-AppLibAppVAppPublishedEventCommand -ApplicationName "BBC Ticker" -RepositoryTypeValue 1 -ApplicationUid 23
```
#### Description
Tracks that fact that BBC Ticker was published from a Microsoft App-V Server package repository
### Example 2
```
New-AppLibAppVAppPublishedEventCommand -ApplicationName "Notepad" -RepositoryTypeValue 2 -ApplicationUid 23
```
#### Description
Tracks that fact that BBC Ticker was published from a Citrix AppLibrary package repository
