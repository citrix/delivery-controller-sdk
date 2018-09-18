# Get-HypConnectionRegion

   Enumerates the regions of a hypervisor connection that are based on cloud technology.

## Syntax
```
Get-HypConnectionRegion [-LiteralPath] <String> [-AdminAddress <String>] [<CommonParameters>]
```

## Detailed Description
   Use this command to enumerate the available regions within a public or private cloud, when making hypervisor connections to cloud services. Sometimes, regions need to be selected and applied before the cloud connection can be used in a meaningful way. This cmdlet allows the supported regions to be listed so that one may be selected.

Once a region has been chosen, use the standard Set-Item provider cmdlet to select it. See the examples for further details.

This cmdlet may return no output, in which case the cloud connection can be considered "regionless" (or, implicitly, all within a single region). In such cases, there is no need to select a region, and the hypervisor connection can be used as is.

## Related Commands
  * [Set-Item](Set-Item/)
## Parameters

| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| LiteralPath | Specifies the path to the hypervisor connection whose regions are being examined. This cmdlet is valid only for hypervisor connections that have the UsesCloudInfrastructure flag set to true. The path must be in one of the following formats: <drive>:\Connections\<ConnectionName> or  <drive>:\Connections\{<Connection Uid>} | true | true (ByValue) |  |
| AdminAddress | Specifies the address of a XenDesktop controller to which the PowerShell snap-in connects. You can provide a host name or an IP address. | false | false | LocalHost. When a value is provided by any cmdlet, this value becomes the default. |

## Input Type
### System.string<br>    You can pipe a string that contains a path to Get-HypConnectionRegion (LiteralPath parameter).
   
## Return Values
### Citrix.Host.Sdk.HypervisorRegion
   Get-HypConnectionRegion returns zero or more instances of the HypervisorConnectionRegion object, each of which contain the following properties:<br>Name <string> Specifies the unique name of the region. Endpoint <string> Specifies the URL endpoint that is specific to the region, if relevant. This may be an empty string, and is returned only for information purposes.<br>A full list of the hypervisor networks that are exposed for use in the hosting unit.## Notes
   In the case of failure, the following errors can be produced.<br>    Error Codes<br>    -----------<br>    ConnectionsPathInvalid<br>    The path provided is not to an item in the Connections subdirectory of the host service provider.<br>    HypervisorConnectionObjectNotFound<br>    The path provided could not be resolved to an existing hypervisor connection. The name or GUID is invalid.<br>    HypervisorInMaintenanceMode<br>    The hypervisor for the connection is in maintenance mode.<br>    ConnectionIsNotCloud<br>    The hypervisor connection is not associated with cloud infrastructure, making it invalid to enumerate regions.<br>    DatabaseError<br>    An error occurred in the service while attempting a database operation.<br>    DatabaseNotConfigured<br>    The operation could not be completed because the database for the service is not configured.<br>    DataStoreException<br>    An error occurred in the service while attempting a database operation. Communication with the database failed for<br>    various reasons.<br>    CommunicationError<br>    An error occurred while communicating with the service.<br>    PermissionDenied<br>    The user does not have administrative rights to perform this operation.<br>    ExceptionThrown<br>    An unexpected error occurred. To locate more details, see the Windows event logs on the controller being used, or examine the XenDesktop logs.
## Examples

### EXAMPLE 1
```
c:\PS>Get-HypConnectionRegions -LiteralPath XDHyp:\Connections\AWS

          RegionName           : us-east-1
          Endpoint             : ec2.us-east-1.amazonaws.com

          RegionName           : us-west-1
          Endpoint             : ec2.us-west-1.amazonaws.com

          RegionName           : eu-west-1
          Endpoint             : ec2.eu-west-1.amazonaws.com

          (...)

          c:\PS>Set-Item -Path XDHyp:\Connections\AWS -Region "us-east-1"
```
   Description<br>-----------<br>This sequence of commands enumerates the available regions of an Amazon AWS cloud connection, and then selects one of them for use in the connection.
