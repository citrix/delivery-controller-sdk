
# Start-Citrixcallhomeupload
Requests the Citrix Telemetry Service to upload the collected data to the Citrix Insight Services (CIS) or to copy the data to a folder (for manual upload to CIS).
## Syntax
```
Start-CitrixCallHomeUpload [-Credential] <PSCredential> [-InputPath <String>] [-Description <String>] [-IncidentTime <String>] [-SRNumber <String>] [-Name <String>] [-UploadHeader <String>] [-AppendHeaders <String>] [-Collect <String>] [<CommonParameters>]

Start-CitrixCallHomeUpload -UploadGrantToken <String> [-InputPath <String>] [-Description <String>] [-IncidentTime <String>] [-SRNumber <String>] [-Name <String>] [-UploaderHeader <String>] [-AppendHeaders <String>] [-Collect <String>] [<CommonParameters>]

Start-CitrixCallHomeUpload -UploadToken <String> [-InputPath <String>] [-Description <String>] [-IncidentTime <String>] [-SRNumber <String>] [-Name <String>] [-UploaderHeader <String>] [-AppendHeaders <String>] [-Collect <String>] [<CommonParameters>]

Start-CitrixCallHomeUpload -OutputPath <String> [-InputPath <String>] [-Description <String>] [-IncidentTime <String>] [-SRNumber <String>] [-Name <String>] [-UploaderHeader <String>] [-AppendHeaders <String>] [-Collect <String>] [<CommonParameters>]
```
## Detailed Description
The Start-CitrixCallHomeUpload cmdlet request an upload of the collected diagnostic data.

If the Credential parameter is specified, the upload is directed to the Citrix Insight Services (CIS).

If the UploadGrantToken parameter is specified, the upload is directed to the Citrix Insight Services (CIS). A valid CIS upload grant token obtained using New-CitrixCallHomeUploadGrantToken must be provided.

If the UploadToken parameter is specified, the upload is directed to the Citrix Insight Services (CIS). A valid CIS upload grant token obtained using New-CitrixCallHomeUploadToken must be provided.

If the OutputPath parameter is specified, the upload is directed to the specified file. The data may then be uploaded manually using the CIS web site.

The optional InputPath parameter may be set to the path to a zip file that will be included in the uploaded bundle.

The Description and Incident Time provide some basic information about this upload request. Set the SRNumber to the Citrix Technical Support incident number.

The Name parameter provides the default file name that is used when you download the bundle from the CIS web site.

The diagnostic data uploaded is determined by the service.

The optional UploadHeader parameter accepts a json-formatted string, which specify the upload headers passed to CIS.

The optional AppendHeaders parameter accepts a json-formatted string, which specify the appended headers uploaded to CIS.

The optional Collect parameter accepts a json-formatted string, which specify the parameters passed to collectors. Current collectors consist of 'sfb', 'wmi', 'process', 'registry', 'crashreport', 'trace', 'file', localdata' and 'sitedata'. Each of the collectors accepts at least a parameter 'enabled', used to disable the collector. By default, all collectors are enabled except for the 'sfb' collector, because 'sfb' collector is used for users to diagnose the skype failure and designed to be on-demand.

'sfb' collector supports three parameters 'account', 'accounts' and 'enabled', first two of which specify the target user(s) 'sfb' collector will collect skype logs for, and can not coexist. If 'sfb' parameter is not null in -Collect json string, the 'sfb' collector will be enabled unless the 'enabled' is false.

'file' collector supports two parameters 'input' and 'enabled', 'input' is an array of string, which means the file paths that are going to be injected into the upload bundle, it has the same effect of '-InputPath'. the 'file' collector will be enabled unless the 'enabled' is false.

The upload may take a long time to finish. If the cmdlet times out, the system event log can be used to check the status of the upload. The upload request may be rejected if the service is already performing an upload.


## Related Commands

* [Get-Credential](./Get-Credential/)
* [New-CitrixCallHomeUploadGrantToken](./New-CitrixCallHomeUploadGrantToken/)
* [New-CitrixCallHomeUploadToken](./New-CitrixCallHomeUploadToken/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| UploadGrantToken | Citrix Call Home upload grant token return from New-CitrixCallHomeUploadGrantToken. | true | True (ByValue and ByPropertyName) |  |
| UploadToken | Citrix Call Home upload token return from New-CitrixCallHomeUploadToken. | true | True (ByValue and ByPropertyName) |  |
| OutputPath | A file name for the service write the diagnostic data to. The file should be specified with a .zip extension as the package is a ZIP file. | true | True (ByValue and ByPropertyName) | false |
| InputPath | The path to a .zip file to include in the uploaded data bundle. | false | true (ByPropertyName) |  |
| Description | A brief description of the reason for the upload. You should provide any general information such information that could help Citrix Technical Support to analyze the data. | false | True (ByPropertyName) |  |
| IncidentTime | The approximate time at which the incident of concern occurred. This helps Citrix Technical Support focus thee analysis the data. If this is not specified, it is set the current local time. | false | True (ByPropertyName) |  |
| SRNumber | Specifies Citrix Technical Support incident number | false | true (ByPropertyName) |  |
| Name | A name used to identify this upload (or set of related uploads). This is the default file name when you download the bundle from the CIS web site. | false | true (ByPropertyName) |  |
| UploadHeader |  | false | true (ByPropertyName) |  |
| AppendHeaders |  | false | true (ByPropertyName) |  |
| Collect | Specify the parameters passed to collectors. Json-formatted. | false | true (ByPropertyName) |  |
| Streaming | Specify the parameter boolean parameter to enable/disable Streaming of upload bundles. Streaming is enabled by default. | false | true (ByPropertyName) |  |
| ParallelCollection | Specify the boolean parameter to enable/disable Parallel Collection of upload bundles. Parallel Collection is enabled by default. | false | true (ByPropertyName) |  |
| CDFControlTraces | Specify the location of CDF Traces to be injected with CallHome bundle. | false | true (ByPropertyName) |  |

## Input Type

### System.String
This cmdlet accepts a string as input that populates the Description parameter.
### System.String
This cmdlet accepts a string as input that populates the IncidentTime parameter.
### System.String
This cmdlet accepts a string as input that populates the Name parameter.
### System.String
This cmdlet accepts a string as input that populates the UploadGrantToken parameter.
### System.String
This cmdlet accepts a string as input that populates the UploadToken parameter.
### System.String
This cmdlet accepts a string as input that populates the OutputPath parameter.
### System.String
This cmdlet accepts a string as input that populates the InputPath parameter.
### System.String
This cmdlet accepts a string as input that populates the Collect parameter.
## Return Values

### 

## Notes
Check system event log to find out more status about the upload request.
## Examples

### Example 1: Upload Diagnostic Data To Citrix Insight Services
```
C:\PS>$uploadGrantToken = New-CitrixCallHomeUploadGrantToken -Credential (Get-Credential)

C:\PS>Start-CitrixCallHomeUpload -UploadGrantToken $uploadGrantToken -InputPath "c:\Diagnostics\ExtraData.zip" -Description "Registration failures with PVS VDAs" -IncidentTime "14:30" -SRNumber 123456 -Name "RegistrationFailure-021812016" -Collect "{'wmi':{'enabled':false}}" -UploadHeader "{'key1':'value1'}" -AppendHeaders "{'key2':'value2'}"
```This command requests a upload of the diagnostic data (exclude the data from wmi collector) to the Citrix CIS site using credentials entered by the interactive user. The estimated incident time is 2:30 PM for the Citrix Technical Support case 123456.&lt;br&gt;The file "c:\\Diagnostics\\ExtraData.zip" will be incorporated into the uploaded bundle.
### Example 2: Export The Diagnostic Data To A File
```
C:\PS>Start-CitrixCallHomeUpload -OutputPath \\mynetwork\myshare\mydata.zip -InputPath "c:\Diagnostics\ExtraData.zip" -Description "Diagnostics for incident number 223344" -IncidentTime "8:15" -SRNumber 223344
```This command requests that the diagnostic data for incident 223344 that occurred near 8:15 AM to be written to mydata.zip. The file "c:\\Diagnostics\\ExtraData.zip" will be incorporated into the uploaded bundle.
### Example 3: Upload Skype For Business Logs To Citrix Insight Services
```
C:\PS>Start-CitrixCallHomeUpload -Credential (Get-Credential) -Description "Skype login failure" -Collect "{'sfb':{'account':'domain\\user1'}}"

C:\PS>Start-CitrixCallHomeUpload -Credential (Get-Credential) -Description "Skype login failures" -Collect "{'sfb':{'accounts':['domain\\user1', 'domain\\user2']}}"
```The first command requests upload of the diagnostic data (including the skype logs for domain user user1) to the Citrix CIS site using credentials entered by the interactive user. The 'sfb' parameter enable the collection and upload of skype logs. The second one is same as the first one except for it will collect skype logs for two domain users: user1 and user2.
### Example 4: Include Cdf Traces Along With Diagnostic Data
```
C:\PS>Start-CitrixCallHomeUpload -Credential (Get-Credential) -CDFControlTraces @("C:\CDFControl\CDFControl_log_02.09.2016_10-58-33", "C:\CDFControl\CDFControl_log_21.09.2016_17-20-33")

C:\PS>Start-CitrixCallHomeUpload -Credential (Get-Credential) -CDFControlTraces "C:\CDFControl"
```CDFControlTraces parameter is used to inject CDF Traces in CallHome data. The CDF output needs to be generated using CDFControl tool.&lt;br&gt;First command takes multiple input paths as array of string, each path corresponds to output location of CDFControl Traces from single seesion.&lt;br&gt;Second example takes only one input path, i.e. the parent directory and auto-detects all the CDFControl traces present within that directory. So in this case it will upload all the CDF traces present under C:\\CDFControl\\ .
