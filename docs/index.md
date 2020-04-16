# XenApp and XenDesktop 7.18 SDK

> **Note:**
> 
> The SDK delivered with this release does not contain any changes since XenApp and XenDesktop version 7.15 LTSR

XenApp and XenDesktop provide an SDK based on a number of Microsoft
Windows PowerShell version 3.0 snap-ins that allows you to perform the
same tasks as you would with the Citrix Studio console, together with
tasks you cannot do with Studio alone.

## Differences in policy rules

There are differences between the SDK and the Studio console in terms of
policy rules. Entitlement and assignment policy rules are independent
entities in the SDK; in the console, these entities are not visible as
they are seamlessly merged with the Delivery Group. Also, access policy
rules are less restrictive in the SDK.

## Use the SDK

The SDK comprises of a number of PowerShell snap-ins installed
automatically by the installation wizard when you install the Controller
or Studio components.

To access and run the cmdlets:

1.Start a shell in PowerShell 3.0.

> To start a shell from the console, click **Studio**, select the
> PowerShell tab, and click on **Launch PowerShell**.
>
> You must run the shell or script using an identity that has Citrix
> administration rights. Although members of the local administrators
> group on the Controller automatically have full administrative
> privileges to allow XenDesktop to be installed, Citrix recommends that
> for normal operation, you create Citrix administrators with the
> appropriate rights, rather than use the local administrators account.

2.To use SDK cmdlets within scripts, set the execution policy in PowerShell.

> For more information about PowerShell execution policy, see your
> Microsoft documentation.

3.Add the snap-ins you require into the PowerShell environment using
    the **Add -PSSnapin** command in the Windows PowerShell console. V1
    and V2 denote the version of the snap-in (XenDesktop 7 snap-ins are version 2.). For example, type:

> Add-PSSnapin Citrix.ADIdentity.Admin.V2
>
> To import all the cmdlets, type:
>
> Add-PSSnapin Citrix.\*.Admin.V\*
>
> After importing, you have access to the cmdlets and their associated
> help.

For an example of a typical use case, see [Get started with the
SDK](./getting-started.md).

## Group Policy SDK usage

The Citrix Group Policy SDK allows you to display and configure Group
Policy settings and filters. It uses a PowerShell provider to create a
virtual drive that corresponds to the machine and user settings and
filters. The provider appears as an extension to New-PSDrive. To use the
Group Policy SDK, either Studio or the XenApp and XenDesktop SDK must be
installed.

**Adding the Group Policy SDK**

1.To add the Group Policy SDK, type:

```
Add-PSSnapin citrix.common.grouppolicy
```
<br>          
2.To access help, type:

```
help New-PSDrive -path localgpo:/
```

**Using the Group Policy SDK**

1.To create a virtual drive and load it with settings, type:

```  
New-PSDrive &lt;Standard Parameters&gt; \[-PSProvider\]
CitrixGroupPolicy *-Controller* &lt;string&gt;
```

```
**New-PSDrive &lt;Standard Parameters&gt; \[-PSProvider\]
CitrixGroupPolicy ***-Controller*** &lt;string&gt;**
```

> where *-Controller* is the fully qualified domain name of a controller
> in the site you want to connect to and load settings from.
