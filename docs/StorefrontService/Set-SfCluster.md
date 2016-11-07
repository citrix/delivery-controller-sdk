# Set-SfCluster

   Sets the parameters on the given cluster.

## Syntax
```
Set-SfCluster -ClusterId <Guid> [-StorefrontUrl <Uri>] [-FarmName <String>] [-XmlServices <Uri[]>] [-RunAsynchronously <Boolean>] [-LoggingId <Guid>] [-AdminAddress <String>] [<CommonParameters>]
```

## Detailed Description
   Sets the parameters on the given cluster and propagate the changes to all servers within a given cluster.

## Related Commands
  * [Get-SfCluster](Get-SfCluster.html)
  * [New-SfCluster](New-SfCluster.html)
  * [Add-SfServerToCluster](Add-SfServerToCluster.html)
  * [Remove-SfServerFromCluster](Remove-SfServerFromCluster.html)
## Parameters

| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| ClusterId | The if of the cluster to perform operation on. | true | false |  |
| StorefrontUrl | The url that will be used by Receivers to contact Storefront. Http or https absolute urls are accepted. | false | false | Server name and http binding. |
| FarmName | Name of the farm that will be used within Store service.  Either both FarmName and XmlServices need to be specified or none of them. | false | false |  |
| XmlServices | Collection of the url of xml services that will be used inside a farm. The urls neeed to be http or https, be absolute and share the same schema and port.  Either both FarmName and XmlServices need to be specified or none of them. | false | false |  |
| RunAsynchronously | If set, the command will run asynchronously. | false | false | false |
| LoggingId | Specifies the identifier of the high-level operation this cmdlet call forms a part of. Citrix Studio and Director typically create high-level operations. PowerShell scripts can also wrap a series of cmdlet calls in a high-level operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller the PowerShell snap-in will connect to. You can provide this as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type
### 
   
## Return Values
### Citrix.Storefront.Sdk.Task or Citrix.Storefront.DataModel.Cluster
   Returns cluster description or a task, if ran asynchronously.
## Examples

### EXAMPLE 1
```
Set-SfCluster -StorefrontUrl http://SfUrl -ClusterId (Guid) -RunAsynchronously $true
```
   Description<br>-----------<br>Sets a Storefront Url in a Cluster with id (Guid). Propagates changes to all servers that are part of the cluster.
