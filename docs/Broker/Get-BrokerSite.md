# Get-BrokerSite

   Gets the current XenDesktop broker site.

## Syntax
```
Get-BrokerSite [-AdminAddress <String>] [<CommonParameters>]
```

## Detailed Description
   The Get-BrokerSite cmdlet gets the current broker site.

The broker site is a top-level, logical representation of the XenDesktop site, from the perspective of the brokering services running within the site. It defines various site-wide default attributes used by the brokering services.

A XenDesktop installation has only a single broker site instance.


-------------------------- BrokerSite Object
The BrokerSite object represents logical representation of the XenDesktop site. It contains the following properties:

    -- BaseOU (System.Guid?)
       The objectGUID property identifying the base OU in Active Directory used for desktop registrations.

    -- BrokerServiceGroupUid (System.Guid)
       The Uid for the Broker Service Group.

    -- ColorDepth (Citrix.Broker.Admin.SDK.ColorDepth)
       The default color depth for new desktop groups.

    -- ConfigLastChangeTime (System.DateTime)
       The time the broker configuration was changed.

    -- ConfigurationServiceGroupUid (System.Guid?)
       The Uid for the Configuration Service Group.

    -- ConnectionLeasingEnabled (System.Boolean?)
       The indicator for connection leasing active.

    -- DefaultMinimumFunctionalLevel (Citrix.Broker.Admin.SDK.FunctionalLevel?)
       The default minimum functional level used for new catalogs and desktop groups when no explicit value is provided.

    -- DesktopGroupIconUid (System.Int32)
       The default desktop icon used for new desktop groups.

    -- DnsResolutionEnabled (System.Boolean)
       The setting to configure whether numeric IP address or the DNS name to be present in the ICA file.

    -- IsSecondaryBroker (System.Boolean)
       Reserved for internal use.

    -- LicensedSessionsActive (System.Int32?)
       The count of active licensed session.

    -- LicenseEdition (System.String)
       The license edition for session brokering.

    -- LicenseGraceSessionsRemaining (System.Int32?)
       The count of License Grace Session Remaining

    -- LicenseModel (Citrix.Broker.Admin.SDK.LicenseModel?)
       The licensing model in use. Values can be 'Concurrent' or 'UserDevice'

    -- LicenseServerName (System.String)
       The DNS for License Server Name

    -- LicenseServerPort (System.Int32)
       The port for the License Server

    -- LicensingBurnIn (System.String)
       The date for the license to end in yyyy.MMdd format

    -- LicensingBurnInDate (System.DateTime?)
       The date for the license to end

    -- LicensingGraceHoursLeft (System.Int32?)
       The number of grace hours left after license expiry

    -- LicensingGracePeriodActive (System.Boolean?)
       The indicator for licensing grace period active

    -- LicensingOutOfBoxGracePeriodActive (System.Boolean?)
       The indicator for licensing out of the box grace period active

    -- LocalHostCacheEnabled (System.Boolean)
       The indicator that the Local Host Cache feature is switched on

    -- MetadataMap (System.Collections.Generic.Dictionary<string, string>)
       The metadata for this command.

    -- Name (System.String)
       The name of the site

    -- PeakConcurrentLicenseUsers (System.Int32?)
       The peak number of concurrent license users

    -- SecureIcaRequired (System.Boolean)
       The default SecureICA usage requirements for new desktop groups.

    -- TotalUniqueLicenseUsers (System.Int32?)
       The total count of license users

    -- TrustManagedAnonymousXmlServiceRequests (System.Boolean)
       The XML Service managed anonymous settings.

    -- TrustRequestsSentToTheXmlServicePort (System.Boolean)
       The XML Service trust settings.

## Related Commands
  * [Set-BrokerSite](Set-BrokerSite/)
  * [Get-BrokerIcon](Get-BrokerIcon/)
## Parameters

| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |

## Input Type
### None
   You cannot pipe input into this cmdlet.
## Return Values
### Citrix.Broker.Admin.SDK.Site
   Get-BrokerSite returns the single broker site instance.
## Examples

### EXAMPLE 1
```
C:\PS> Get-BrokerSite
```
   Description<br>-----------<br>Gets the current broker site.
