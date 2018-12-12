
# Get-Liclocalizednames
Gets the friendly name of the products and license types saved on License Server.
## Syntax
```
Get-LicLocalizedNames [-AdminAddress] <String> [-Locale <String>] [-CertHash <String>] [<CommonParameters>]
```
## Detailed Description
Returns the friendly name of the products and license types (in the requested locale), which are stored on the License Server.


## Related Commands

## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| AdminAddress | Specifies the Web Services for Licensing address of the License Server that the PowerShell Snap-in will connect to.  Retrieve this address with Get-LicLocation. | true | true (ByValue) |  |
| Locale | Language code of localized human readable strings. | false | false | en |
| CertHash | Specifies the hash of the License Server certificate needing verification. | false | false |  |

## Input Type

### System.String

## Return Values

### Citrix.Licensing.Admin.Sdk.Wsllocalizednames

## Notes
If the command fails, one of the following errors is returned.<br>            Error Codes<br>            -----------<br>            LicensingAdminStatus.CommunicationError<br>                There was a problem communicating with the License Server.<br>            LicensingAdminStatus.InvalidCertificate<br>                Certificate is not verified or it is self-signed. Get the Certificate and store the Hash in Ccs.<br>            LicensingAdminStatus.CertificateVerificationFailed<br>                Certificate is not verified or it is self-signed. Get the Certificate and store the Hash in Ccs.<br>            LicensingAdminStatus.UnknownError<br>                An unexpected error occurred.  For more details, see the Windows event logs on the controller
## Examples

### Example 1
```
PS C:\>$cert = Get-LicCertificate -AdminAddress https://licserver.mydomain.net:8083

PS C:\>$loc = Get-LicLocalizedNames -AdminAddress https://licserver.mydomain.net:8083 -CertHash $cert.CertHash -Locale en
```Returns the friendly products and license types name stored on the License Server in English.&lt;br&gt;Output:&lt;br&gt;PS C:\\&gt; \$loc&lt;br&gt;Features                                                          LicenseTypes&lt;br&gt;--------                                                          ------------&lt;br&gt;{XDT\_PLT\_UD, XDT\_PLT\_CCS, XDT\_ENT\_UD, XDT\_ENT\_CCS...}             {DE, TP, Eval, RetailS...}&lt;br&gt;PS C:\\&gt; \$loc.Features&lt;br&gt;FeatureName     ProductNameandEdition                    ModelName               Version&lt;br&gt;-----------     ---------------------                    ---------               -------&lt;br&gt;XDT\_PLT\_UD      Citrix XenDesktop Platinum               User/Device             1.0&lt;br&gt;XDT\_PLT\_CCS     Citrix XenDesktop Platinum               Concurrent              2.0&lt;br&gt;XDT\_ENT\_UD      Citrix XenDesktop Enterprise             User/Device             1.0&lt;br&gt;XDT\_ENT\_CCS     Citrix XenDesktop Enterprise             Concurrent              2.0&lt;br&gt;XDT\_APP\_UD      Citrix XenDesktop App                    User/Device             1.0&lt;br&gt;XDT\_ADV\_UD      Citrix XenDesktop Advanced               User/Device             1.0&lt;br&gt;XDT\_STD\_UD      Citrix XenDesktop VDI                    User/Device             2.0&lt;br&gt;XDT\_STD\_CCS     Citrix XenDesktop VDI                    Concurrent              3.0&lt;br&gt;XDS\_PLT\_CCS     Citrix XenDesktop Platinum               Concurrent (Legacy)     3.0&lt;br&gt;XDS\_ENT\_CCS     Citrix XenDesktop Enterprise             Concurrent (Legacy)     3.0&lt;br&gt;XDS\_ADV\_CCS     Citrix XenDesktop Advanced               Concurrent (Legacy)     3.0&lt;br&gt;XDS\_STD\_CCS     Citrix XenDesktop VDI                    Concurrent (Legacy)     4.0&lt;br&gt;CTXLSDIAG       Citrix License Server Diagnostics...     Server                  1.0&lt;br&gt;CITRIX          Citrix Start-up License                  Server                  1.0&lt;br&gt;PS C:\\&gt; \$loc.LicenseTypes&lt;br&gt;TypeName                FriendlyName                   Version&lt;br&gt;--------                ------------                   -------&lt;br&gt;DE                      Developer Edition              1.0&lt;br&gt;TP                      Technology Preview             1.0&lt;br&gt;Eval                    Evaluation                     1.0&lt;br&gt;RetailS                 Expiring Retail                1.0&lt;br&gt;Retail                  Retail                         1.0&lt;br&gt;NFR                     Not For Resale                 1.0&lt;br&gt;SYS                     System                         1.0
