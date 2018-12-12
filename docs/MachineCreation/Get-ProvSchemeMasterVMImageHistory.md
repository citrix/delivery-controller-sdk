
# Get-Provschememastervmimagehistory
Gets the list of master VM snapshots that have been used to provide hard disks to provisioning schemes.
## Syntax
```
Get-ProvSchemeMasterVMImageHistory [-ProvisioningSchemeName <String>] [-ProvisioningSchemeUid <Guid>] [-MasterImageVM <String>] [-VMImageHistoryUid <Guid>] [-ImageStatus <String>] [-ShowAll] [-ReturnTotalRecordCount] [-MaxRecordCount <Int32>] [-Skip <Int32>] [-SortBy <String>] [-Filter <String>] [-BearerToken <String>] [-AdminAddress <String>] [<CommonParameters>]
```
## Detailed Description
Provides the ability to discover the master VM snapshots used to provide the hard disk image for provisioning schemes.  This information includes the date and time when the image was introduced.

By default, this cmdlet returns only those snapshots that have been used previously.  This information can be used to roll back a provisioning scheme to a previous image.

The ShowAll parameter may be supplied to also show the snapshot for the image currently in use, and the snapshots for any images prepared for later use.


## Related Commands

* [Publish-ProvMasterVMImage](./Publish-ProvMasterVMImage/)
* [Remove-ProvSchemeMasterVMImageHistory](./Remove-ProvSchemeMasterVMImageHistory/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| ProvisioningSchemeName | The name of the provisioning scheme. | false | false |  |
| ProvisioningSchemeUid | The unique identifier of the provisioning scheme. | false | false |  |
| MasterImageVM | The path to the snapshot item in the hosting unit PowerShell provider. | false | false |  |
| VMImageHistoryUid | The unique identifier for the Image History item. | false | false |  |
| ImageStatus | The status of the provisioning scheme image. | false | false |  |
| ShowAll | Show all images. This includes images currently in use, and images prepared for later use. | false | false | false |
| ReturnTotalRecordCount | See about\_Prov\_Filtering for details. | false | false | false |
| MaxRecordCount | See about\_Prov\_Filtering for details. | false | false | false |
| Skip | See about\_Prov\_Filtering for details. | false | false | 0 |
| SortBy | See about\_Prov\_Filtering for details. | false | false |  |
| Filter | See about\_Prov\_Filtering for details. | false | false |  |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snap-in connects to.  You can provide this as a host name or an IP address. | false | false | LocalHost. When a value is provided by any cmdlet, this value becomes the default. |

## Input Type

### 

## Return Values

### Citrix.Machinecreation.Sdk.Vmimage
This object represents a master VM history. It contains the following parameters:<br>    VMImageHistoryUid &lt;Guid&gt;<br>        The unique identifier for the History item.<br>    ProvisioningSchemeUid &lt;Guid&gt;<br>        The unique identifier for the provisioning scheme that the VM was used for.<br>    ProvisioningSchemeName &lt;string&gt;<br>        The name of the provisioning scheme that the VM was used for.<br>    MasterImageVM &lt;string&gt;<br>        The path to the Snapshot item that was used as the master VM image.<br>    Date &lt;DateTime&gt;<br>        The date and time that the VM or snapshot was used in the provisioning scheme.<br>    ImageStatus &lt;string&gt;<br>        The status of the provisioning scheme image.<br>    MasterImageId &lt;string&gt;<br>        The unique identifier for the snapshot, as assigned by the hosting unit.<br>    FunctionalLevel &lt;string&gt;<br>        The FunctionalLevel of the VDA installed on the VM.
## Notes
In the case of failure, the following errors can result.<br>    Error Codes<br>    -----------<br>    PartialData<br>    Only a subset of the available data was returned.<br>    PermissionDenied<br>    The user does not have administrative rights to perform this operation.<br>    ConfigurationLoggingError<br>    The operation could not be performed because of a configuration logging error.<br>    CouldNotQueryDatabase<br>    The query required to get the database was not defined.<br>    CommunicationError<br>    An error occurred while communicating with the service.<br>    DatabaseNotConfigured<br>    The operation could not be completed because the database for the service is not configured.<br>    InvalidFilter<br>    A filtering expression was supplied that could not be interpreted for this cmdlet.<br>    ExceptionThrown<br>    An unexpected error occurred.  To locate more details, see the Windows event logs on the controller being used or examine the XenDesktop logs.
## Examples

### Example 1
```
C:\PS>Get-ProvSchemeMasterVMImageHistory

VMImageHistoryUid      : 3cba3a75-89cd-4868-989b-27feb378fec5

ProvisioningSchemeUid  : 7585f0de-192e-4847-a6d8-22713c3a2f42

ProvisioningSchemeName : MyScheme

MasterImageVM          : /Base.vm/base.snapshot

Date                   : 17/05/2010 09:27:50
```
#### Description
Gets all the hard disk images that have been used across all provisioning schemes.
### Example 2
```
C:\PS>Get-ProvSchemeMasterVMImageHistory -ProvisioningSchemeName MyScheme -masterImageVM "/BaseXp.vm/update1.snapshot" | Publish-ProvMasterVMImage
```
#### Description
Roll back the provisioning scheme to use the hard disk from the update1.snapshot for the provisioning scheme called "MyScheme".
