# Set-BrokerDesktopGroup

   Adjusts the settings of a broker desktop group.

## Syntax
```
Set-BrokerDesktopGroup [-InputObject] <DesktopGroup[]> [-PassThru] [-AppDisks <Guid[]>] [-AutomaticPowerOnForAssigned <Boolean>] [-AutomaticPowerOnForAssignedDuringPeak <Boolean>] [-ColorDepth <ColorDepth>] [-DeliveryType <DeliveryType>] [-Description <String>] [-Enabled <Boolean>] [-IconUid <Int32>] [-InMaintenanceMode <Boolean>] [-IsRemotePC <Boolean>] [-MinimumFunctionalLevel <FunctionalLevel>] [-OffPeakBufferSizePercent <Int32>] [-OffPeakDisconnectAction <SessionChangeHostingAction>] [-OffPeakDisconnectTimeout <Int32>] [-OffPeakExtendedDisconnectAction <SessionChangeHostingAction>] [-OffPeakExtendedDisconnectTimeout <Int32>] [-OffPeakLogOffAction <SessionChangeHostingAction>] [-OffPeakLogOffTimeout <Int32>] [-PeakBufferSizePercent <Int32>] [-PeakDisconnectAction <SessionChangeHostingAction>] [-PeakDisconnectTimeout <Int32>] [-PeakExtendedDisconnectAction <SessionChangeHostingAction>] [-PeakExtendedDisconnectTimeout <Int32>] [-PeakLogOffAction <SessionChangeHostingAction>] [-PeakLogOffTimeout <Int32>] [-ProtocolPriority <String[]>] [-PublishedName <String>] [-SecureIcaRequired <Boolean>] [-SettlementPeriodBeforeAutoShutdown <TimeSpan>] [-SettlementPeriodBeforeUse <TimeSpan>] [-ShutdownDesktopsAfterUse <Boolean>] [-TimeZone <String>] [-TurnOnAddedMachine <Boolean>] [-ZonePreferences <ZonePreference[]>] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]

Set-BrokerDesktopGroup [-Name] <String> [-PassThru] [-AppDisks <Guid[]>] [-AutomaticPowerOnForAssigned <Boolean>] [-AutomaticPowerOnForAssignedDuringPeak <Boolean>] [-ColorDepth <ColorDepth>] [-DeliveryType <DeliveryType>] [-Description <String>] [-Enabled <Boolean>] [-IconUid <Int32>] [-InMaintenanceMode <Boolean>] [-IsRemotePC <Boolean>] [-MinimumFunctionalLevel <FunctionalLevel>] [-OffPeakBufferSizePercent <Int32>] [-OffPeakDisconnectAction <SessionChangeHostingAction>] [-OffPeakDisconnectTimeout <Int32>] [-OffPeakExtendedDisconnectAction <SessionChangeHostingAction>] [-OffPeakExtendedDisconnectTimeout <Int32>] [-OffPeakLogOffAction <SessionChangeHostingAction>] [-OffPeakLogOffTimeout <Int32>] [-PeakBufferSizePercent <Int32>] [-PeakDisconnectAction <SessionChangeHostingAction>] [-PeakDisconnectTimeout <Int32>] [-PeakExtendedDisconnectAction <SessionChangeHostingAction>] [-PeakExtendedDisconnectTimeout <Int32>] [-PeakLogOffAction <SessionChangeHostingAction>] [-PeakLogOffTimeout <Int32>] [-ProtocolPriority <String[]>] [-PublishedName <String>] [-SecureIcaRequired <Boolean>] [-SettlementPeriodBeforeAutoShutdown <TimeSpan>] [-SettlementPeriodBeforeUse <TimeSpan>] [-ShutdownDesktopsAfterUse <Boolean>] [-TimeZone <String>] [-TurnOnAddedMachine <Boolean>] [-ZonePreferences <ZonePreference[]>] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
```

## Detailed Description
   The Set-BrokerDesktopGroup cmdlet is used to disable or enable an existing broker desktop group or to alter its settings.

## Related Commands
  * [Get-BrokerDesktopGroup](Get-BrokerDesktopGroup.html)
  * [New-BrokerDesktopGroup](New-BrokerDesktopGroup.html)
  * [Rename-BrokerDesktopGroup](Rename-BrokerDesktopGroup.html)
  * [Remove-BrokerDesktopGroup](Remove-BrokerDesktopGroup.html)
## Parameters

| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| InputObject | Specifies the desktop groups to adjust. | true | true (ByValue) |  |
| Name | Specifies the desktop groups to adjust, based on their Name property. | true | true (ByPropertyName) |  |
| PassThru | This cmdlet does not generate any output, unless you use the PassThru parameter, in which case it returns the affected record. | false | false | False |
| AppDisks | Specifies the application disks to be used by machines in the desktop group. | false | false |  |
| AutomaticPowerOnForAssigned | Specifies whether assigned desktops in the desktop group should be automatically started at the start of peak time periods. Only relevant for groups whose DesktopKind is Private. | false | false |  |
| AutomaticPowerOnForAssignedDuringPeak | Specifies whether assigned desktops in the desktop group should be automatically started throughout peak time periods. Only relevant for groups whose DesktopKind is Private and which have AutomaticPowerOnForAssigned set to true. | false | false |  |
| ColorDepth | Specifies the color depth that the ICA session should use for desktops in this group.  Valid values are FourBit, EightBit, SixteenBit, and TwentyFourBit. | false | false |  |
| DeliveryType | Specifies whether desktops, applications, or both, can be delivered from machines contained within the desktop group. Desktop groups with a DesktopKind of Private cannot be used to deliver both desktops and applications.<br>When changing the delivery type to desktops only, there must be no remaining desktop-hosted applications associated with the group, or application-specific assignment/entitlement policy rules for the group.<br>When changing the delivery type to applications only, there must be no remaining client-hosted applications associated with the group, or desktop-specific assignment/entitlement policy rules for the group.<br>Valid values are DesktopsOnly, AppsOnly, and DesktopsAndApps. | false | false |  |
| Description | A description for this desktop group useful for administrators of the site. | false | false |  |
| Enabled | Whether the desktop group should be in the enabled state; disabled desktop groups do not appear to users. | false | false |  |
| IconUid | The UID of the broker icon to be displayed to users for their desktop(s) in this desktop group. | false | false |  |
| InMaintenanceMode | Whether the desktop should be put into maintenance mode; a desktop group in maintenance mode will not allow users to connect or reconnect to their desktops. | false | false |  |
| IsRemotePC | Supplies a new value for IsRemotePC.<br>IsRemotePC can only be enabled when:<br>o SessionSupport is SingleSession<br>o DeliveryType is DesktopsOnly<br>o DesktopKind is Private<br>IsRemotePC can be switched from true to false only if no RemotePC relationship exists between a catalog and this desktop group. | false | false |  |
| MinimumFunctionalLevel | The new minimum FunctionalLevel required for machines to work successfully in the desktop group. If this is higher than the FunctionalLevel of any machines already in the desktop group, they will immediately cease to function. | false | false |  |
| OffPeakBufferSizePercent | The percentage of machines in the desktop group that should be kept available in an idle state outside peak hours. | false | false |  |
| OffPeakDisconnectAction | The action to be performed after a configurable period of a user session disconnecting outside peak hours. Possible values are Nothing, Suspend, or Shutdown. | false | false |  |
| OffPeakDisconnectTimeout | The number of minutes before the configured action should be performed after a user session disconnects outside peak hours. | false | false |  |
| OffPeakExtendedDisconnectAction | The action to be performed after a second configurable period of a user session disconnecting outside peak hours. Possible values are Nothing, Suspend, or Shutdown. | false | false |  |
| OffPeakExtendedDisconnectTimeout | The number of minutes before the second configured action should be performed after a user session disconnects outside peak hours. | false | false |  |
| OffPeakLogOffAction | The action to be performed after a configurable period of a user session ending outside peak hours. Possible values are Nothing, Suspend, or Shutdown. | false | false |  |
| OffPeakLogOffTimeout | The number of minutes before the configured action should be performed after a user session ends outside peak hours. | false | false |  |
| PeakBufferSizePercent | The percentage of machines in the desktop group that should be kept available in an idle state in peak hours. | false | false |  |
| PeakDisconnectAction | The action to be performed after a configurable period of a user session disconnecting in peak hours. Possible values are Nothing, Suspend, or Shutdown. | false | false |  |
| PeakDisconnectTimeout | The number of minutes before the configured action should be performed after a user session disconnects in peak hours. | false | false |  |
| PeakExtendedDisconnectAction | The action to be performed after a second configurable period of a user session disconnecting in peak hours. Possible values are Nothing, Suspend, or Shutdown. | false | false |  |
| PeakExtendedDisconnectTimeout | The number of minutes before the second configured action should be performed after a user session disconnects in peak hours. | false | false |  |
| PeakLogOffAction | The action to be performed after a configurable period of a user session ending in peak hours. Possible values are Nothing, Suspend, or Shutdown. | false | false |  |
| PeakLogOffTimeout | The number of minutes before the configured action should be performed after a user session ends in peak hours. | false | false |  |
| ProtocolPriority | A list of protocol names in the order in which they should be attempted for use during connection. | false | false |  |
| PublishedName | The name that will be displayed to users for their desktop(s) in this desktop group. | false | false |  |
| SecureIcaRequired | Whether HDX connections to desktops in the new desktop group require the use of a secure protocol. | false | false |  |
| SettlementPeriodBeforeAutoShutdown | Time after a session ends during which automatic shutdown requests (for example, shutdown after use, idle pool management) are deferred. Any outstanding shutdown request takes effect after the settlement period expires. This is typically used to configure time to allow logoff scripts to complete. | false | false |  |
| SettlementPeriodBeforeUse | Idle period before a machine can be selected to host a new session after registration or the end of a previous session. This is typically used to allow a machine to become idle following processing associated with start-up or logoff actions. A machine may still be selected during the idle period if no other machine is available for immediate use. | false | false |  |
| ShutdownDesktopsAfterUse | Whether desktops in this desktop group should be automatically shut down when each user session completes (only relevant to power-managed desktops). | false | false |  |
| TimeZone | The time zone in which this desktop group's machines reside.<br>The time zone must be specified for any of the group's automatic power management settings to take effect. Automatic power management operations include pool management (power time schemes), reboot schedules, session disconnect and logoff actions, and powering on assigned machines etc. | false | false |  |
| TurnOnAddedMachine | This flag specifies whether the Broker Service should attempt to power on machines when they are added to the desktop group. | false | false |  |
| ZonePreferences | Ordered list of zone preferences to be applied when launching resources from this desktop group. Valid zone preference values are UserLocation, UserHome, UserHomeOnly and ApplicationHome.<br>The list can have zero or more entries subject to the following restrictions: Zone preferences can only be applied to groups having a DesktopKind of Shared; the same zone preference value cannot occur in the list more than once; the UserHome and UserHomeOnly values are mutually exclusive and cannot both appear in the list. | false | false |  |
| LoggingId | Specifies the identifier of the high level operation that this cmdlet call forms a part of. Desktop Studio and Desktop Director typically create High Level Operations. PowerShell scripts can also wrap a series of cmdlet calls in a High Level Operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |

## Input Type
### Citrix.Broker.Admin.SDK.DesktopGroup
   You can pipe the desktop groups to be adjusted to Set-BrokerDesktopGroup.
## Return Values
### None or Citrix.Broker.Admin.SDK.DesktopGroup
   This cmdlet does not generate any output, unless you use the PassThru parameter, in which case it generates a Citrix.Broker.Admin.SDK.DesktopGroup object.
## Examples

### EXAMPLE 1
```
C:\PS> Set-BrokerDesktopGroup EMEA* -InMaintenanceMode $true -PassThru
```
   Description<br>-----------<br>Sets all desktop groups with names starting "EMEA" into maintenance mode, returning the set of desktop groups.
### EXAMPLE 2
```
C:\PS> Get-BrokerDesktopGroup -InMaintenanceMode $true | Set-BrokerDesktopGroup -Enabled $false
```
   Description<br>-----------<br>Disable all desktop groups that are in maintenance mode.
