﻿# Get-SfCluster

   Gets all Storefront clusters present in the site.

## Syntax
```
Get-SfCluster [-AdminAddress <String>] [<CommonParameters>]
```

## Detailed Description
   Gets all Storefront clusters present in the site. There is one special Cluster with null id that lists the servers that are not part to any cluster (they are available to join any).

## Related Commands
  * [New-SfCluster](New-SfCluster/)
  * [Add-SfServerToCluster](Add-SfServerToCluster/)
  * [Remove-SfServerFromCluster](Remove-SfServerFromCluster/)
  * [Set-SfCluster](Set-SfCluster/)
## Parameters

| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| AdminAddress | Specifies the address of a XenDesktop controller the PowerShell snap-in will connect to. You can provide this as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type
### 
   
## Return Values
### Citrix.Storefront.DataModel.Cluster[]
   Returns array of clusters available in current deployment.
## Examples

### EXAMPLE 1
```

```
   Description<br>-----------
