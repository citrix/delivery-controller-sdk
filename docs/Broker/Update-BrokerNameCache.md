# Update-BrokerNameCache

   Performs administrative operations on the user and machine name cache.

## Syntax
```
Update-BrokerNameCache [-Machines] [-Users] [-AdminAddress <String>] [<CommonParameters>]
```

## Detailed Description
   Triggers an immediate asynchronous refresh of the name cache. This may be useful to ensure up-to-date name information is present in the cache after user and/or machine accounts are known to have changed and you need to see those changes immediately instead of waiting for the periodic automatic refresh.

The Broker Service maintains a cache of the names of users and machines in use by the site. By default, name information is obtained periodically from Active Directory and the cache refreshed automatically.

During normal usage, you should not need to perform administrative operations on the name cache.

For users/groups, the following name information is cached: 
    Windows name (DOMAIN\user) 
    User Principal Name or 'UPN' (user@upndomain) 
    Full Name or 'Common Name' (typically a user's full name)

For machines, the following name information is cached: 
    Windows name (DOMAIN\machine) 
    DNS name (machine.dnsdomain)

## Related Commands
## Parameters

| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| Machines | Triggers an asynchronous refresh of all cached machine name information. | false | false |  |
| Users | Triggers an asynchronous refresh of all cached user name information. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |

## Input Type
### None
   You cannot pipe input into this cmdlet.
## Return Values
### None
   ## Notes
   For some user accounts, for example, the built-in domain administrator, the UPN and/or Full Name values may not be available because they are not typically specified within Active Directory.<br>    For group accounts, UPN and Full Name values are not available because they are not applicable or not specified within Active Directory.<br>    The DNS name information for a machine is obtained from Active Directory and not from the DNS sub-system. If a machine has only recently been configured, the DNS information may not be available initially.
## Examples

### EXAMPLE 1
```
C:\PS> Update-BrokerNameCache -Machines
```
   Description<br>-----------<br>Triggers an immediate asynchronous refresh of all machine name information held within the name cache.
### EXAMPLE 2
```
C:\PS> Update-BrokerNameCache -Machines -Users
```
   Description<br>-----------<br>Triggers an immediate asynchronous refresh of all machine and user name information held within the name cache.
