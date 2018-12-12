﻿
# about\_HypStorage

## Topic
about\_HypStorage


## Short Description
The HypStorage object defines parameters for a hosting unit. The parameters specify a storage tier definition made up of the storage type and one or more storage locations. When created it is assigned a job group uid with the -JobGroup parameter.

The HypStorage can then be used with a subsequent New-Item operation via the -JobGroup reference.


## Long Description
A HypStorage object defines a set of parameters for a hosting unit. The parameters specify a storage tier definition and the HypStorage can then be used with a subsequent New-Item operation via the -JobGroup reference.

-JobGroup &lt;Uid&gt; Specifies the unique id of the new job group

-StoragePath &lt;String&gt; Specifies one or more paths in a connection to storage items that are used when the Machine Creation Service creates new virtual machines.

-StorageType &lt;storage type&gt; Specifies the type of the new storage tier. Currently the only storage type supported is TemporaryStorage.

Once added to the HostingUnit with the New-Item cmdlet, the additional storage can subsequently be modified or removed with the Add-HypHostingUnitStorage, Set-HypHostingUnitStorage and Remove-HypHostingUnitStorage cmdlets.


## Examples
To create a HypStorage and use it when defining a new Hosting Unit


```
	# Get a unique id for the job group 
    $job = [Guid]::NewGuid() 

```

```
	# Define the Storage tier 
    New-HypStorage -JobGroup $job -StorageType TemporaryStorage -StoragePath @('XDHyp:\Connections\MyConnection\Primary Storage.storage') 

```

```
	# Use it in the New-Item call 
    New-Item -HypervisorConnectionName 'MyConnection' -JobGroup $job -NetworkPath @('XDHyp:\Connections\MyConnection\Network 1.network') <additional New-Item parameters...> 

```

## Related Links
about\_HypHostSnapin Add-HypHostingUnitStorage Remove-HypHostingUnitStorage Set-HypHostingUnitStorage New-Item


