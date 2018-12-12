﻿
# Set-Brokersite
Changes the overall settings of the current XenDesktop broker site.
## Syntax
```
Set-BrokerSite [-PassThru] [-BaseOU <Guid>] [-ColorDepth <ColorDepth>] [-ConnectionLeasingEnabled <Boolean>] [-DefaultMinimumFunctionalLevel <FunctionalLevel>] [-DesktopGroupIconUid <Int32>] [-DnsResolutionEnabled <Boolean>] [-LocalHostCacheEnabled <Boolean>] [-ReuseMachinesWithoutShutdownInOutageAllowed <Boolean>] [-SecureIcaRequired <Boolean>] [-TrustManagedAnonymousXmlServiceRequests <Boolean>] [-TrustRequestsSentToTheXmlServicePort <Boolean>] [-LoggingId <Guid>] [-AdminAddress <String>] [-BearerToken <String>] [<CommonParameters>]
```
## Detailed Description
The Set-BrokerSite cmdlet modifies properties of the current broker site.

The broker site is a top-level, logical representation of the XenDesktop site, from the perspective of the brokering services running within the site. It defines various site-wide default attributes used by the brokering services.

A XenDesktop installation has only a single broker site instance.


## Related Commands

* [Get-BrokerSite](./Get-BrokerSite/)
* [New-BrokerIcon](./New-BrokerIcon/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| PassThru | This cmdlet does not generate any output, unless you use the PassThru parameter, in which case it returns the affected record. | false | false | False |
| BaseOU | Changes the objectGUID property identifying the base OU in Active Directory used for desktop registrations. For sites using only registry-based discovery (the default) this value is \$null.<br>Any desktop attempting to register through a different OU from the one specified here is rejected. Note that desktops configured for registry-based discovery can register with the site, even if a BaseOU value is specified.<br>Information held in Active Directory is not modified by changing this value.<br>Typically, this property is changed only by using the Set-ADControllerDiscovery.ps1 script. | false | false |  |
| ColorDepth | Changes the default color depth for new desktop groups, if no color depth is specified explicitly when a group is created. Changing this default has no impact on the color depths used already by existing groups.<br>Valid values are FourBit, EightBit, SixteenBit, and TwentyFourBit. | false | false |  |
| ConnectionLeasingEnabled | Enabled or disable connection leasing on the site. | false | false |  |
| DefaultMinimumFunctionalLevel | Changes the default minimum functional level used for new catalogs and desktop groups when no explicit value is provided. | false | false |  |
| DesktopGroupIconUid | Changes the default desktop icon used for new desktop groups if no icon is specified explicitly when a group is created. Changing this default has no impact on the icons used already by existing groups.<br>The specified icon must already have been added to the site using New-BrokerIcon. | false | false |  |
| DnsResolutionEnabled | Changes whether ICA files returned by a broker service to a user device contain the numeric IP address or the DNS name of the desktop machine to which a session should be established.<br>With the default value (\$false), ICA files will always contain a numeric IP address. To have DNS names appear in the ICA files, set the value to \$true.<br>Even when DNS resolution is enabled (\$true), IP addresses may still appear in ICA files. The reasons for this include, for example, that the broker service is unable to obtain a DNS name for the target machine, or that Storefront is configured to always use numeric IP addresses in this context. | false | false |  |
| LocalHostCacheEnabled | If the Local Host Cache feature is available, this property enables or disables it at run-time. | false | false |  |
| ReuseMachinesWithoutShutdownInOutageAllowed | Allows the ReuseMachinesWithoutShutdownInOutage setting on individual DesktopGroups to be enabled. Because these settings have potential security implications, only the site administrator can enable use of this feature.  Disabling this setting will clear corresponding field on all delivery groups. | false | false |  |
| SecureIcaRequired | Changes the default SecureICA usage requirements for new desktop groups if no SecureICA setting is specified explicitly when a group is created. Changing this default has no impact on the SecureICA usage requirements of existing groups. | false | false |  |
| TrustManagedAnonymousXmlServiceRequests | Changes whether the XML Service (as used by Storefront) implicitly trusts managed anonymous launch requests.<br>With the default value (\$false), any attempt to use the XML service for managed anonymous sessions is rejected.<br>If this setting is enabled, anyone with access to the XML service will be able to utilize the managed anonymous functionality to leave disconnected prelaunched anonymous sessions available for reconnection. You must ensure that controllers running the brokering services are securely firewalled. | false | false |  |
| TrustRequestsSentToTheXmlServicePort | Changes whether the XML Service (as used by Storefront) implicitly trusts the originator of requests it receives, or whether it fully authenticates them.<br>With the default value (\$false), full authentication checks are performed. However, you must enable this setting (\$true) to allow support for "Pass-through" authentication, and/or connections routed through Access Gateway.<br>If this setting is enabled, you must ensure that controllers running the brokering services are securely firewalled. | false | false |  |
| LoggingId | Specifies the identifier of the high level operation that this cmdlet call forms a part of. Desktop Studio and Desktop Director typically create High Level Operations. PowerShell scripts can also wrap a series of cmdlet calls in a High Level Operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |

## Input Type

### None
You cannot pipe input into this cmdlet.
## Return Values

### None Or Citrix.Broker.Admin.Sdk.Site
This cmdlet does not generate any output, unless you use the PassThru parameter, in which case it generates a Citrix.Broker.Admin.SDK.Site object.
## Examples

### Example 1
```
C:\PS> Set-BrokerSite -ColorDepth SixteenBit
```
#### Description
Specifies that any new desktop groups created, where a color depth value is not specified, default to using 16-bit color depth for user sessions to desktops or applications within that group.
