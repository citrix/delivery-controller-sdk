# New-AcctIdentityPool

   Creates a new identity pool.

## Syntax
```
New-AcctIdentityPool -IdentityPoolName <String> [-NamingScheme <String>] [-NamingSchemeType <ADIdentityNamingScheme>] [-OU <String>] [-Domain <String>] [-AllowUnicode] [-StartCount <Int32>] [-Scope <String[]>] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
```

## Detailed Description
   Provides the ability to create identity pools that can be used to store AD computer accounts.

The naming scheme, naming scheme type, and domain must be specified if the identity pool is to be used to create new accounts.

Each identity pool is tied to a single domain. All the identities in an identity pool belong to the same domain. If the domain is not specified by a parameter to this command the domain will be set when an account is imported into it.

## Related Commands
  * [Remove-AcctIdentityPool](Remove-AcctIdentityPool.html)
  * [Rename-AcctIdentityPool](Rename-AcctIdentityPool.html)
  * [Set-AcctIdentityPool](Set-AcctIdentityPool.html)
  * [Test-AcctIdentityPoolNameAvailable](Test-AcctIdentityPoolNameAvailable.html)
  * [New-AcctADAccount](New-AcctADAccount.html)
## Parameters

| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| IdentityPoolName | The name of the identity pool.  This must not contain any of the following characters \/;:#.*?=<>|[]()""' | true | false |  |
| NamingScheme | Defines the template name for AD accounts created in the identity pool.  The scheme can consist of fixed characters and a variable part defined by '#' characters.  There can be only one variable region defined. The number of '#' characters defines the minimum length of the variable region. For example, a naming scheme of H#### could create accounts called H0001, H0002 (for a numeric scheme type) or HAAAA, HAAAB (for an alphabetic type).<br>Citrix recommends that you define a naming scheme that will not clash with accounts which already exist in AD; account creation will fail if a clash occurs.<br>There are restrictions on what constitutes a valid computer name: Minimum name length: 2 (DNS) Maximum name length: 15 bytes (NetBIOS) The following characters are not allowed in a computer name: backslash (\) slash mark (/) colon (:) asterisk (*) question mark (?) quotation mark (") less than sign (<) greater than sign (>) vertical bar (|) comma (,) tilde (~) exclamation point (!) at sign (@) number sign (#) dollar sign ($) percent (%) caret (^) ampersand (&) apostrophe (') parenthesis (()) braces ({}) underscore (_) The following names are reserved and must not be used at the end of the naming scheme: -GATEWAY -GW -TAC Names must not start with a period (NetBIOS). Names must not be composed entirely of numbers (NetBIOS). Names must not contain a blank or space characters (DNS). | false | false |  |
| NamingSchemeType | The type of naming scheme.  This can be Numeric or Alphabetic.  This defines the format of the variable part of the AD account names that will be created. | false | false | Numeric |
| OU | The OU that computer accounts will be created into. If this is not specified, accounts are created into the default account container specified by AD.  This is the 'Computers' container for out-of-the-box installations of AD.  The OU must be a valid AD container and of the domain specified for the pool; | false | false |  |
| Domain | The AD domain name for the pool.  Specify this in FQDN format; for example, MyDomain.com. | false | false |  |
| AllowUnicode | Allow the naming scheme to have characters other than alphanumeric characters. | false | false |  |
| StartCount | Defines the next number that will be used if creating new AD accounts for the identity pool. | false | false |  |
| Scope | The administration scopes to be applied to the new identity pool. | false | false |  |
| LoggingId | Specifies the identifier of the high-level operation this cmdlet call forms a part of. Citrix Studio and Director typically create high-level operations. PowerShell scripts can also wrap a series of cmdlet calls in a high-level operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snap-in connects to.  You can provide this as a host name or an IP address. | false | false | LocalHost. Once a value is provided by any cmdlet, this value becomes the default. |
| ZoneUid | Represents the UID from a zone object returned by the get-ConfigZone cmdlet. | false | false |  |

## Input Type
### 
   
## Return Values
### Citrix.ADIdentity.Sdk.IdentityPool<br>    This object provides details of the identity pool and contains the following information:<br>IdentityPoolName <string><br>    The name of the identity pool.<br>IdentityPoolUid <Guid><br>    The unique identifier for the identity pool.<br>NamingScheme <string><br>    The naming scheme for the identity pool.<br>NamingSchemeType <Citrix.XDInterServiceTypes.ADIdentityNamingScheme><br>    The naming scheme type for the identity pool. This can be one of the following:<br>        Numeric - naming scheme uses numeric indexes<br>        Alphabetic - naming scheme uses alphabetic indexes<br>StartCount <int><br>    The next index to be used when creating an identity from the identity pool.<br>OU <string><br>    The Active Directory distinguished name for the OU in which accounts created from this identity pool will be created.<br>Domain <string><br>    The Active Directory domain that accounts in the pool belong to.<br>Lock <Boolean><br>    Indicates if the identity pool is locked.
   ## Notes
   In the case of failure, the following errors can result.<br>    Error Codes<br>    -----------<br>    UnableToConvertDomainName<br>    Unable to convert domain name to DNS format.<br>    NamingSchemeNotEnoughCharacters<br>    Naming scheme does not have enough characters specified.<br>    NamingSchemeTooManyCharacters<br>    Naming scheme has too many characters specified.<br>    NamingSchemeIllegalCharacter<br>    Naming scheme contains illegal characters.<br>    NamingSchemeMayNotStartWithPeriod<br>    Naming scheme starts with a period (.) character.<br>    NamingSchemeMayNotBeAllNumbers<br>    Naming scheme contains only numbers.<br>    NamingSchemeMissingNumericSpecifications<br>    Naming scheme does not contain any variable specification (i.e. no '#' characters are specified).<br>    NamingSchemeHasMoreThanOneSetOfHashes<br>    Naming scheme has more than one variable region (i.e. there are '#' characters separated by other characters).<br>    IdentityPoolDuplicateObjectExists<br>    An identity pool with the same name already exists.<br>    IdentityPoolOUInvalid<br>    Identity Pool OU invalid as it does not exist.<br>    IdentityPoolOUOfWrongDomain<br>    IdentityPool OU invalid as it refers to a different domain to the domain specified for the pool.<br>    InvalidIdentityPoolParameterCombination<br>    Caused by either of the following validation errors:<br>    * If an OU is specified then a domain must also be specified.<br>    * NamingScheme, NamingSchemeType and Domain must all be present if any of these are specified.<br>    NamingSchemeIllegalComputerName<br>    The naming scheme supplied is not valid.<br>    PermissionDenied<br>    The user does not have administrative rights to perform this operation.<br>    ConfigurationLoggingError<br>    The operation could not be performed because of a configuration logging error<br>    DatabaseError<br>    An error occurred in the service while attempting a database operation.<br>    DatabaseNotConfigured<br>    The operation could not be completed because the database for the service is not configured.<br>    ServiceStatusInvalidDb<br>    An error occurred in the service while attempting a database operation - communication with the database failed for<br>    for various reasons.<br>    CommunicationError<br>    An error occurred while communicating with the service.<br>    ExceptionThrown<br>    An unexpected error occurred.  To locate more details, see the Windows event logs on the controller being used or examine the XenDesktop logs.
## Examples

### EXAMPLE 1
```
c:\PS>New-AcctIdentityPool -IdentityPoolName MyPool -NamingScheme Acc#### -Domain MyDomain.com -NamingSchemeType Numeric


IdentityPoolName : MyPool
IdentityPoolUid  : 22072d9e-6a8f-494b-a5bc-2ef18ca4b915
NamingScheme     : Acc####
NamingSchemeType : Numeric
StartCount       : 1
OU               :
Domain           : MyDomain.com
Lock             : False
```
   Description<br>-----------<br>Create a new identity pool from which accounts can be created in the domain called "MyDomain.com" using a numeric scheme of the format Acc####.  The first account that will be created from this identity pool definition is Acc0001.<br>New AD accounts can be imported into this pool too, but must be from the Domain "MyDomain.com".
