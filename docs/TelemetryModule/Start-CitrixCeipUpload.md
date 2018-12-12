
# Start-Citrixceipupload
Requests the Citrix Telemetry Service to upload ceip data to the Citrix Insight Services (CIS) or to copy the data to a folder (for manual upload to CIS).
## Syntax
```
Start-CitrixCeipUpload -OutputPath <String> [<CommonParameters>]
```
## Detailed Description
The Start-CitrixCeipUpload cmdlet request an upload of the collected anonymous data.

If the OutputPath parameter is specified, the upload is directed to the specified file. The data may then be uploaded manually using the CIS web site.


## Related Commands

## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| OutputPath | A file name for the service write the diagnostic data to. The file should be specified with a .zip extension as the package is a ZIP file. | true | True (ByValue and ByPropertyName) | false |
| Streaming | Specify the parameter boolean parameter to enable/disable Streaming of upload bundles. Streaming is enabled by default. | false | true (ByPropertyName) |  |
| ParallelCollection | Specify the parameter boolean parameter to enable/disable Parallel Colelction of upload bundles. Parallel Collection is enabled by default. | false | true (ByPropertyName) |  |

## Input Type

### System.String
This cmdlet accepts a string as input that populates the OutputPath parameter.
## Return Values

### 

