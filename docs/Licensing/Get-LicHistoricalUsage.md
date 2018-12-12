
# Get-Lichistoricalusage
Gets the historical usage details for the requested products.
## Syntax
```
Get-LicHistoricalUsage [-AdminAddress] <String> [-StartDate <DateTime>] [-EndDate <DateTime>] [-Products <String[]>] -SADate <String> [-CertHash <String>] [<CommonParameters>]
```
## Detailed Description
Returns the historical usage details between start and end dates for requested products with specified Customer Success Services (CSS Date) in requested locale.


## Related Commands

## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| AdminAddress | Specifies the Web Services for Licensing address of the License Server that the PowerShell Snap-in will connect to.  Retrieve this address with Get-LicLocation. | true | true (ByValue) |  |
| StartDate | Specifies the start date of  the historical usage data being requested. | false | false | 01/01/1970 |
| EndDate | Specifies the end date of the historical usage data being requested. | false | false | Current Date and Time |
| Products | Array of Products for which historical data is to be collected. If not specified, historical data for all the products is collected. | false | false | All Product Edition Model |
| SADate | The required Customer Success Services date (CSS Date) of the product. | true | false |  |
| CertHash | Specifies the hash of the License Server certificate to be verified | false | false |  |

## Input Type

### System.String

## Return Values

### Citrix.Licensing.Admin.Sdk.Wslhistoricalusage

## Notes
If the command fails, one of the following errors is returned.<br>            Error Codes<br>            -----------<br>            LicensingAdminStatus.CommunicationError<br>                There was a problem communicating with the License Server.<br>            LicensingAdminStatus.InvalidCertificate<br>                Certificate Is Not Verified It is Self-Signed. So Get The Certificate And Store The Hash In Ccs.<br>            LicensingAdminStatus.CertificateVerificationFailed<br>                Certificate Is Not Verified Its Self-Signed. So Get The Certificate And Store The Hash In Ccs.<br>            LicensingAdminStatus.UnknownError<br>                An unexpected error occurred.  For more details, see the Windows event logs on the controller.<br>           LicensingAdminStatus.InvalidSADateFormat<br>                The required Customer Success Services date format is incorrect.<br>           LicensingAdminStatus.InvalidStartDateOrEndDate<br>                StartDate is after EndDate.<br>    	   LicensingAdminStatus.InvalidProductEditionModelFormat<br>                ProductEditionModel format is wrong.
## Examples

### Example 1
```
PS C:\> $cert = Get-LicCertificate -AdminAddress https://licserver.mydomain.net:8083

PS C:\> $startDate = Get-Date -Day 01 -Month 11 -Year 2014

PS C:\> $endDate = Get-Date -Day 28 -Month 02 -Year 2015

PS C:\>

PS C:\> $historicalusg =  Get-LicHistoricalUsage -AdminAddress https://licserver.mydomain.net:8083 -StartDate $startDate -EndDate $endDate -SADate 2015.0218 -Products @("XDT_ENT_UD", "XDT_PLT_UD") -CertHash $cert.CertHash
```Returns the historical usage about XDT\_ENT\_UD and XDT\_PLT\_UD between 1st Nov, 2014 and 28th Feb, 2015&lt;br&gt;Output:&lt;br&gt;PS C:\\ &gt; \$historicalusg&lt;br&gt;LSVersion              : v11.12.1.0 build 146690 (ipv6) i86\_n3&lt;br&gt;MacAddress             : 40-A8-F0-55-CD-6C&lt;br&gt;EarliestDateOfSample   : 2/13/2015 6:01:40 AM&lt;br&gt;MostRecentDateOfSample : 2/13/2015 10:27:59 AM&lt;br&gt;LicPoolUsage           : {Citrix.Licensing.Admin.SDK.WSLLicensePoolUsage,&lt;br&gt;Citrix.Licensing.Admin.SDK.WSLLicensePoolUsage,&lt;br&gt;Citrix.Licensing.Admin.SDK.WSLLicensePoolUsage,&lt;br&gt;Citrix.Licensing.Admin.SDK.WSLLicensePoolUsage...}&lt;br&gt;PS C:\\&gt; \$historicalusg.LicPoolUsage\[0\].LicPool&lt;br&gt;ProductEditionModel             : XDT\_ENT\_UD&lt;br&gt;CustomerSuccessServicesDate     : 2015.1201&lt;br&gt;ExpirationDate                  : 12/1/2015&lt;br&gt;TotalLicensesIncludingOverDraft : 100&lt;br&gt;OverdraftLicenses               : 10&lt;br&gt;LicenseSerialNos                : 1&lt;br&gt;VendorString                    : ;LT=Retail;GP=720;CL=VDS,VDA,VDE;SA=0;LP=90;ODP=0;NUDURMIN=2880;NUDURMAX=525600&lt;br&gt;LicenseType                     : Retail&lt;br&gt;Notices                         : Citrix Systems Inc.&lt;br&gt;StartDates                      :&lt;br&gt;LicenseIssueDate                : 18-dec-2005&lt;br&gt;PS C:\\&gt; \$historicalusg.LicPoolUsage\[0\].UsgSampleList\[0\]&lt;br&gt;Datetime                         Count&lt;br&gt;--------                         -----&lt;br&gt;2/13/2015 6:01:40 AM                 0
