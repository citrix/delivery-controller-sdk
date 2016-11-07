# about_HypHostSnapIn
## TOPIC
    about_HypHostSnapin 

## SHORT DESCRIPTION
    The Host Service PowerShell snap-in provides administrative functions for 
    the Host Service. 

## COMMAND PREFIX
    All commands in this snap-in have the noun prefixed with 'Hyp'. 

## LONG DESCRIPTION
    The Host Service PowerShell snap-in enables both local and remote 
    administration of the Host Service. It lets you 
    configure XenDesktop deployments to make use of hypervisors, networks, and 
    storage, and enables browsing of their contents using the Host PowerShell 
    provider (Citrix.HypervisorProvider). 

    The provider creates a default PSDrive with a drive identifier of 'XDHyp'. 
    This drive provides two root folders: 

    HostingUnits Folder 
        Contains a list of all the hosting units that have been defined using 
        the new-Item provider command. 

        Hosting units define not only a hypervisor connection, but also 
        reference networks and storage. Hosting units are used by the Machine 
        Creation Service to provide the information required to create and 
        manage virtual machines that can be used by other services. A hosting 
        unit references a root path. This is a specific point in the provider 
        connection tree. The hosting unit is constrained to provide only items 
        below this point in the tree. This restricts the locations that the 
        Machine Creation Service can use to create virtual machines and the 
        networks and storage that can be used. 

    Connections Folder 
        Contains a list of all the hosting unit connections that are 
        defined using the new-Item provider command. 

        Change directory to a specific connection and use the dir/Get-ChildItem 
        command to list all of the infrastructure (such as folders, hypervisors, 
        networks, storage, and virtual machines) that is available in the 
        hosting unit to which the connection refers. The paths to these items 
        are used as the input to commands in the Host Service and Machine 
        Creation Service snap-ins. 

    The contents of the Hosting Unit and Connection folders reflect the content 
    and structure of the hypervisor to which they refer. The item extensions 
    reflect the object type for each item. Not all item types are appropriate 
    for all hypervisor types. Possible item types are: 

        Virtual Machine (.vm) 
        Snapshot (.snapshot) 
        Cluster (.cluster) 
        Host (.host) 
        HostGroup (.hostgroup) 
        DataCenter (.datacenter) 
        Folder (.folder) 
        ResourcePool (.resourcepool) 
        ComputeResource (.computeresource) 

    When used with a path that refers to the Host provider (with a default 
    drive of 'XDHyp:'), the Host provider extends the standard New-Item, 
    Get-Item, Get-ChildItem, Remove-Item, Rename-Item, and Set-Item commands as 
    described below. For more information about the basic behavior of these 
    commands, see the help for the command. The Move-Item and Copy-Item 
    commands are not supported for the Host provider. 

    New-Item 
        The following parameters are available when using New-Item in the 
        Connections directory (or a path that refers to the directory). The 
        Credential parameter is not supported. 

        -Name 
            Specifies the name of the connection, which must not contain any of 
            the following characters: \/;:#.*?=<>|[]()"'{}. The Name parameter 
            is optional but, if not included, the connection name must be 
            specified as part of the Path parameter. 

        -HypervisorAddress <String[]> 
            Specifies an array of addresses that can be used to contact the 
            required hypervisor. All the addresses are considered equivalent, 
            that is, all of the addresses provide access to the same virtual 
            machines, snapshots, network, and storage. 

        -ConnectionType <ConnectionType> 
            Specifies the type of hypervisor that the connection is for. 
            Supported hypervisor types are: 

                XenServer 
                SCVMM (Microsoft Hyper-V) 
                vCenter (VMware vSphere/ESX) 
                Custom 

        -PluginId <String> 
            Specifies the class name for the Citrix Managed Machine library 
            that is used to access the hypervisor. You can obtain this list 
            using the Get-HypHypervisorPlugin command. The PluginId 
            parameter must be specified if the ConnectionType is set to 
            'Custom'. 

        -UserName <String>, -Password <String>, -SecurePassword <SecureString> 
            Specifies the credentials for the connection to the hypervisor. You 
            can specify the password as either Password or SecurePassword, but not 
            both. The UserName parameter, and either Password or SecurePassword, specify 
            the same information as the HypervisorCredential parameter, so use 
            of one precludes use of the other. 

        -HypervisorCredential <PSCredential> 
            Specifies credentials for the connection to the hypervisor. The 
            HypervisorCredential parameter specifies the same information as 
            UserName and either Password or SecurePassword, so use of one 
            precludes use of the other. 

        -Persist 
            Specifies that the connection details are persistent. If this 
            parameter is not included, the connection is held only for the 
            duration of the current runspace and PSDrive combination.  
            Only persistent connection items are visible to administrators in other 
            runspaces and PSDrives. Hosting units cannot be created from 
            connections that are not persistent. 

        -AdminAddress <String> 
            Specifies the address of the Host Service that the command  
            communicates with. After it is set, this address is used for all commands 
            in the Host Service PowerShell snap-in. If this parameter is not 
            included or set by another command, or if Set-HypAdminConnection 
            has not been used, the command attempts to use a local Host 
            Service. 

        -LoggingId <String> 
            Specifies the identifier of the high-level operation that this cmdlet call 
            forms a part of. Citrix Studio and Director typically create 
            high-level operations. PowerShell scripts can also wrap a series of cmdlet 
            calls in a high-level operation by way of the Start-LogHighLevelOperation 
            and Stop-LogHighLevelOperation cmdlets. 

        -Scopes <String[]> 
            Specifies the list of administrative scopes that the new connection will 
            be a part of. The scopes control which administrators are able to 
            work with the connection. 

        -ZoneUid <Uid> 
            Specifies the ZoneUid the connection belongs to. The zone determines which 
            connections are local to the controller. 

        -JobGroup <Uid> 
            Specifies the Uid assocuiated with the HypStorage object created with 
            the New-HypStorage command. This HypStorage object specifies any additional 
            storage details required for the new connection. 

        The following parameters are available when using New-Item in the 
        HostingUnits directory (or a path that refers to the directory). 

        -Name 
            Specifies the name of the hosting unit, which must not contain any 
            of the following characters: \/;:#.*?=<>|[]()"'{}. The Name 
            parameter is optional but, if not included, the hosting unit name 
            must be provided as part of the Path parameter. 

        -HypervisorConnectionName <String> 
            Specifies the name of the connection that the hosting unit  
            uses. To create a hosting unit, the referenced connection must be 
            persistent and the ConnectionType must not be set to 'Custom'. 

        -HypervisorConnectionUid <Guid> 
            Specifies the unique identifier of the connection that the hosting 
            unit uses. To create a hosting unit, the referenced connection 
            must be persistent and the ConnectionType must not be set to 
            'Custom'. 

        -RootPath <String> 
            Specifies the location in a connection that is used as the 
            starting reference for the hosting unit. The path must point to an 
            item in the connection that is marked as a SymLink. The root of a 
            XenServer connection is a special case that is also considered a 
            SymLink. If this parameter is not included, the current location 
            in the provider is used. 

        -NetworkPath <String> 
            Specifies the path in a connection to the network item that 
            is used when the Machine Creation Service creates new virtual 
            machines. 

        -StoragePath <String> 
            Specifies one or more paths in a connection to storage items 
            that are used when the Machine Creation Service creates new 
            virtual machines. After they are set, you can modify storage paths using 
            the Add-HypHostingUnitStorage and Remove-HypHostingUnitStorage 
            commands. If the connection is based on cloud infrastructure, storage 
            items are typically not available, in which case this parameter can 
            be omitted. 
             
        -PersonalvDiskStoragePath <String> 
            Specifies one or more paths in a connection to storage items 
            that are used when the Machine Creation Service creates disks 
            for the virtual machines. After they are set, you can modify storage paths  
            using the Add-HypHostingUnitStorage and Remove-HypHostingUnitStorage 
            commands. 

        -NoVmTagging 
            Specifies that new virtual machines are not tagged with 
            metadata from the hypervisor. By default, all virtual machines 
            created by the Machine Creation Service are tagged to show they are created 
            by XenDesktop. These tags are used by the provider to restrict the 
            list of virtual machines displayed when viewing the content of the 
            Connections or HostingUnit paths. If this parameter is not 
            included, all virtual machines are displayed at all times. 

        -AdminAddress <String> 
            Specifies the address of the Host Service that the command will 
            communicate with. After it is set, this address is used for all commands 
            in the Host Service PowerShell snap-in. If this parameter is not 
            included or set by another command, or if Set-HypAdminConnection 
            has not been used, the command attempts to use a local Host 
            Service. 
             
        -UseLocalStorageCaching 
            When Get-HypServiceAddedCapability indicates that the LocalStorageCaching 
            feature is available, use this parameter to specify that 
            the virtual machines created for this hosting unit will use local 
            storage caching for their disk images. 

        -GpuGroup 
		    Specifies a path to a GPU Group in a connection that will be used when 
			Machine Creation Services creates VMs. Only a single GPU Group is supported 
			and the value is immutable. 

        -LoggingId <String> 
            Specifies the identifier of the high-level operation that this cmdlet call 
            forms a part of. Citrix Studio and Director typically create 
            high-level operations. PowerShell scripts can also wrap a series of cmdlet 
            calls in a high-level operation by way of the Start-LogHighLevelOperation 
            and Stop-LogHighLevelOperation cmdlets. 

        The following parameters are available when using New-Item relative to a 
        connection or hosting unit. 

        -ItemType <string> 
            Specifies the type of item to create when invoked relative to a connection 
            or hosting unit. Supported ItemType values are: 

               SecurityGroup (cloud only) 

        -Description 
            Specifies a description for the security group. 

        -VpcId 
            Specifies a VPC ID for the security group. 

    Get-Item 

    Get-ChildItem (alias dir) 

    Rename-Item 

    Remove-Item 
        The following additional parameters are available. 

        AdminAddress 
            Specifies the address of the Host Service that the command 
            communicates with. After it is set, this address is used for all commands 
            in the Host Service PowerShell snap-in. If this parameter is not 
            included or set by another command, or if Set-HypAdminConnection 
            has not been used, the command attempts to use a local Host 
            Service. 

        -LoggingId <String> 
            Specifies the identifier of the high-level operation that this cmdlet call 
            forms a part of. Citrix Studio and  Director typically create 
            high-level operations. PowerShell scripts can also wrap a series of cmdlet 
            calls in a high-level operation by way of the Start-LogHighLevelOperation 
            and Stop-LogHighLevelOperation cmdlets. 

        You can specify the Path parameter by name or by using the unique 
        identifier for the connection or hosting unit enclosed in braces. 
        For example: 

            -Path XDHyp:\{1233-3213ACDF-12323} 

        The Filter parameter is not supported. Virtual machines created by 
        the Machine Creation Service are returned only if the -Force 
        parameter is used or if virtual machine tagging was disabled on the 
        hosting unit with the NoVmTagging parameter when the VMs were 
        created. 

    Set-Item 
        The following parameters are available when using Set-Item in the 
        Connections directory. 

        -UserName <String>, -Password <String>, -SecurePassword <SecureString> 
            Specifies the credentials for the connection to the hypervisor. The 
            password can be given as either Password or SecurePassword, but not 
            both. The UserName parameter and either Password or SecurePassword specify 
            the same information as the HypervisorCredential parameter, so use 
            of one precludes use of the other. 

        -HypervisorCredential <PSCredential> 
            Specifies credentials for the connection to the hypervisor.  The 
            HypervisorCredential parameter specifies the same information as 
            the UserName parameter and either Password or SecurePassword, so use of one 
            precludes use of the other. 
             
        -HypervisorAddress <string[]> 
            Specifies the addresses of the hypervisor that this connection represents. 
            This replaces all existing addresses. 

        -LoggingId <String> 
            Specifies the identifier of the high-level operation that this cmdlet call 
            forms a part of. Citrix Studio and Director typically create 
            high-level operations. PowerShell scripts can also wrap a series of cmdlet 
            calls in a high-level operation by way of the Start-LogHighLevelOperation 
            and Stop-LogHighLevelOperation cmdlets. 

        -MaintenanceMode <Boolean> 
            Places the connection into maintenance mode which disables all communication 
            between XenDesktop and the Hypervisor. Use this mode when making changes to the 
            hypervisor; for instance, if the password for the access account needs to be changed. 

        -AdminAddress <String> 
            Specifies the address of the Host Service that the command 
            communicates with. After it is set, this address is used for all commands 
            in the Host Service PowerShell snap-in. If this parameter is not 
            included or set by another command, or if Set-HypAdminConnection 
            has not been used, the command tries to use a local Host 
            Service. 
             
        The Credential parameter is not supported. Addresses can be modified 
        with the Add-HypHypervisorConnectionAddress and 
        Remove-HypHypervisorConnectionAddress commands. Metadata can be 
        modified with the Add-HypMetadata and Remove-HypMetadata commands. 

        The following parameters are available when using New-Item in the 
        HostingUnits directory. 

        -Name 
            Specifies the name of the hosting unit, which must not contain any 
            of the following characters: \/;:#.*?=<>|[]()"'{}. The Name 
            parameter is optional but, if not included, the hosting unit name 
            must be provided as part of the Path parameter. 

        -NetworkPath <String> 
            Specifies the path in a connection to the network item that 
            is used when the Machine Creation Service creates new virtual 
            machines. 

        -NoVmTagging 
            Specifies that new virtual machines are not tagged with 
            metadata from the hypervisor. By default, all virtual machines 
            created by the Machine Creation Service are tagged to show they are created 
            by XenDesktop. These tags are used by the provider to restrict the 
            list of virtual machines displayed when viewing the content of the 
            Connections or HostingUnit paths. If this parameter is not 
            included, all virtual machines are displayed at all times. 

        -AdminAddress <String> 
            Specifies the address of the Host Service that the command 
            communicates with. After it is set, this address is used for all commands 
            in the Host Service PowerShell snap-in. If this parameter is not 
            included or set by another command, or if Set-HypAdminConnection 
            has not been used, the command attempts to use a local Host 
            Service. 
             
        -UseLocalStorageCaching <bool> 
            When Get-HypServiceAddedCapability indicates that the LocalStorageCaching 
            feature is available, use this parameter to specify that 
            the virtual machines created for this hosting unit will use local 
            storage caching for their disk images. 

        -LoggingId <String> 
            Specifies the identifier of the high-level operation that this cmdlet call 
            forms a part of. Citrix Studio and Director typically create 
            high-level operations. PowerShell scripts can also wrap a series of cmdlet 
            calls in a high-level operation by way of the Start-LogHighLevelOperation 
            and Stop-LogHighLevelOperation cmdlets. 

        Storage can be modified with the Add-HypHostingUnitStorage and 
        Remove-HypHostingUnitStorage commands. Metadata can be modified with 
        the Add-HypMetadata and Remove-HypMetadata commands. 

    The item types returned when these commands are used in the Host Service 
    provider are defined in the Object Definitions section below. 

## EXAMPLES
    To Create a Persistent Hypervisor Connection 

        new-item -path "xdhyp:\Connections" -Name MyConn -ConnectionType 
            XenServer -HypervisorAddress "http:\\address" -UserName user 
            -Password password -Persist 

        PSPath:                   Citrix.HostingUnitService.Admin.V1.0\ 
                                  Citrix.Hypervisor::XDHyp:\Connections\MyConn 
        PSParentPath:             Citrix.HostingUnitService.Admin.V1.0\ 
                                  Citrix.Hypervisor::XDHyp:\Connections 
        PSChildName:              MyConn 
        PSDrive:                  XDHyp 
        PSProvider:               Citrix.HostingUnitService.Admin.V1.0\ 
                                  Citrix.Hypervisor 
        PSIsContainer:            True 
        HypervisorConnectionUid:  04e6daa2-5cbd-4491-b70c-6daf733ee82a 
        HypervisorConnectionName: MyConn 
        ConnectionType:           XenServer 
        HypervisorAddress:        {http:\\address} 
        UserName:                 user 
        Persistent:               True 
        PluginId:                 XenFactory 
        SupportsPvsVMs:           True 
        Revision:                 1b0b0d02-bc1b-49d8-b2b0-be6fb7f150ad 
        MaintenanceMode:          False 
        Metadata:                 {MaxAbsoluteActiveActions = 100, 
                                  MaxAbsoluteNewActionsPerMinute = 100, 
                                  MaxPowerActionsPercentageOfDesktops = 20} 

    To Create a Hosting Unit 

        new-item -Path "xdhyp:\HostingUnits" 
            -Name MyHU 
            -HypervisorConnectionName MyConn 
            -RootPath XDHYP:\Connections\MyConn 
            -NetworkPath XDHYP:\Connections\MyConn\Network 0.network 
            -StoragePath XDHYP:\Connections\MyConn\Local storage on 
            myXenServer.storage 

        PSPath:               Citrix.HostingUnitService.Admin.V1.0\ 
                              Citrix.Hypervisor::XDHyp:\HostingUnits\MyHU 
        PSParentPath:         Citrix.HostingUnitService.Admin.V1.0\ 
                              Citrix.Hypervisor::XDHyp:\HostingUnits 
        PSChildName:          MyHU 
        PSDrive:              XDHyp 
        PSProvider:           Citrix.HostingUnitService.Admin.V1.0\ 
                              Citrix.Hypervisor 
        PSIsContainer:        True 
        HostingUnitUid:       df91f886-1141-4280-bd59-2ee260a4df79 
        HostingUnitName:      MyHU 
        HypervisorConnection: MyConn 
        RootPath:             / 
        RootId:                
        NetworkPath:          /Network 0.network 
        NetworkId:            ab47080b-ca15-771a-c8dc-6ad9650158f1 
        Storage:              {/Local storage on myXenServer.storage} 
        VMTaggingEnabled:     True 
        Metadata:             {} 

        Relative paths can be used for all parameters. 

## OBJECT DEFINITIONS
    Citrix.XDInterServiceTypes.HypervisorConnection 
        The hypervisor connection object is returned when a connection item is 
        located. This item has the following parameters. 

        HypervisorConnectionUid <Guid> 
            Specifies the unique identifier for the connection item. 

        HypervisorConnectionName <String> 
            Specifies the name of the connection item. 

        ConnectionType <Citrix.XDInterServiceTypes.ConnectionType> 
            Specifies the type of hypervisor that the connection is for. 
            Supported hypervisor types are: 

                XenServer 
                SCVMM (Microsoft Hyper-V) 
                vCenter (VMware vSphere/ESX) 
                Custom 

        HypervisorAddress <String[]> 
            Specifies the addresses that can be used to contact the 
            required hypervisor. 

        Username <String> 
            Specifies the administrator user name for the connection to the hypervisor  
            (from the user name and password given as administrator credentials when 
             setting up this connection) 

        Persistent <Boolean> 
            Specifies whether or not the connection is persistent. 

        PluginId <String> 
            Specifies the Citrix Managed Machine class identifier for the 
            hypervisor. 

        SupportsPvsVM <Boolean> 
            Specifies whether or not the connection can be used as part of a 
            hosting unit. If this parameter is set to 'True', a hosting unit 
            referencing this connection can be created. 

        Revision <Guid> 
            A unique identifier that is changed every time any properties of 
            the connection are changed. 

        MaintenanceMode <Boolean> 
            Specifies whether or not the connection is currently in maintenance 
            mode. 

        Metadata <Citrix.XDInterServiceTypes.Metadata[]> 
            The collection of metadata associated with the connection. 

    Citrix.XDInterServiceTypes.HostingUnit 
        The hosting unit object is returned when a hosting unit item is 
        located. This item has the following parameters. 

        HostingUnitName <String> 
            Specifies the name of the hosting unit. 

        HostingUnitUid <Guid> 
            Specifies the unique identifier for the hosting unit. 

        HypervisorConnection <Citrix.XDInterServiceTypes.HypervisorConnection> 
            Specifies the hypervisor connection item that the hosting unit 
            references. 

        NetworkId <String> 
            Specifies the unique identifier for the network in the 
            hypervisor context that the hosting unit references. 

        NetworkPath <String> 
            Specifies the path to the network in the Host Service provider. 

        RootId <String> 
            Specifies the unique identifier for the root connection item in 
            the hypervisor context that the hosting unit references. 

        RootPath <String> 
            Specifies the path to the root of the hosting unit from within the 
            Host Service provider. 

        Storage <Citrix.XDInterServiceTypes.Storage[]> 
            Specifies the collection of storage objects that are defined for 
            use as part of the hosting unit. This object contains the 
            following parameters. 

            StorageID <String> 
                Specifies the identifier for the storage in the hypervisor 
                context. 

            StoragePath <String> 
                Specifies the path to the storage in the Host Service 
                provider. 

        VMTaggingEnabled <Boolean> 
            Specifies whether or not virtual machine metadata is used to 
            tag virtual machines created by XenDesktop. 

        Metadata <Citrix.XDInterServiceTypes.Metadata[]> 
            Specifies the collection of metadata associated with the hosting 
            unit. 

    Citrix.HostingUnitService.Sdk.HypervisorObject 
        The hypervisor object is returned when any item is located from within 
        a Connection or HostingUnit folder. This item has the following 
        parameters. 

        AdditionalData <Dictionary<String,String> 
            Stores extra untyped data for the item. This dictionary contains 
            different information for each item type. 

            For Storage Items 
                Key = StorageType 
                Values = Shared or Local 

			For VM Items 
				Key = PowerState 
				Values = PoweredOn, 
					     PoweredOff, 
						 Suspended, 
						 TransitioningToOn, 
						 TransitioningToOff, 
						 Suspending, 
						 Resuming, 
						 Unknown, 
						 Error 

        Name <String> 
            Specifies the name of the item. 

        FullName <String> 
            Specifies the name with the appropriate file extension. 

        ObjectPath <String> 
            Specifies the relative path to the item from the root of the 
            connection of which the item is part. 

        FullPath <String> 
            Specifies the absolute path to the item in the 
            Citrix.Hypervisor provider. 

        Id <String> 
            Specifies the identity of the item in the hypervisor context. 

        IsContainer <Boolean> 
            Specifies whether or not the item can contain other items. 

        IsSymLink <Boolean> 
            Specifies whether or not the item can be used as a RootPath of a 
            hosting unit. 

        ObjectType <Citrix.HostingUnitService.Sdk.NodeType> 
            Specifies the item type. 

## ERROR CODES
    The provider commands can return the following error codes. 

    New-Item 
        ConnectionNameOrUidInvalid 
            The name or unique identifier of the hypervisor connection 
            specified for the hosting unit is invalid. 

        HostingUnitRootPathInvalid 
            The root path specified for the hosting unit is invalid. The root 
            path must be a valid item in the hypervisor tree and a SymLink. 

        HostingUnitNetworkPathInvalid 
            The network path specified for the hosting unit is invalid. The 
            network path must be a valid item in the hypervisor tree and 
            relative to the root path. 

        HostingUnitStoragePathInvalid 
            The storage path specified for the hosting unit is invalid. The 
            storage path must be a valid item in the hypervisor tree and 
            relative to the root path. 

        HostingUnitDuplicateObjectExists 
            A hosting unit object with the same name already exists. Hosting 
            unit names must be unique. 

        HostingUnitStorageDuplicateObjectExists 
            A hosting unit storage object with the same storage path already 
            exists for this hosting unit. There can be only one object for 
            each combination of hosting unit and storage path. 
             
        HypervisorNotContactable 
            The hypervisor could not be contacted at the supplied address, which is 
            either invalid or unreachable. 
             
        HypervisorAddressInvalidFormat 
            The address is not in a valid form for the specified hypervisor 
            type. 

        ConnectionAddressInvalid 
            The specified address is invalid and does not belong to the same  
            pool. 

        HypervisorConnectionDuplicateObjectExists 
            A hypervisor connection object with the same name already exists. 
            Hypervisor connection names must be unique. 

        HypervisorConnectionAddressDuplicateObjectExists 
            A hypervisor connection address object with the same address 
            already exists for this hypervisor connection. There can be only 
            one object for each combination of hypervisor connection and 
            address. 

	    HypervisorConnectionForHostingUnitIsVirtual 
		    The specified hypervisor connection for the hosting unit is a virtual 
			non-persistent connection. A persistent connection is required when 
			creating a hosting unit. 

        InputNameInvalid 
            The name specified for the hosting unit or hypervisor connection 
            is invalid because it contains one or more of the following characters: 
            \/;:#.*?=<>|[]()"'{}. 

        InputPathInvalid 
            The specified path is invalid because it is not in one of the following 
            formats: 

                XDHyp:\Connections\<Name>  
                XDHyp:\Connections\{Guid} 

        ExceptionThrown 
            An unexpected error occurred. 

        DatabaseError 
            There was a problem communicating with the database. 

        CommunicationError 
            There was a problem communicating with the remote service. 

        PermissionDenied 
            The user does not have administrative rights to perform this operation. 

        ScopeNotFound 
            One or more of the scopes nominated for the new connection do not exist. 

        CannotCreateSecurityGroupHere 
            Security groups can only be created in a virtual private cloud (VPC). 

    Get-Item and Get-ChildItem 
        HypervisorConnectionObjectNotFound 
            The hypervisor connection object specified in the path could not be 
            found. 

        HostingUnitObjectNotFound 
            The specified hosting unit object could not be found. 

        HypervisorInMaintenanceMode 
            The hypervisor for the specified connection is currently in 
            maintenance mode and cannot be accessed. 
        FailureToRetrieveConnectionPassword 
            The password for the HypervisorConnection cannot be retrieved or decrypted. 
        ExceptionThrown 
            An unexpected error occurred. 

        DatabaseError 
            There was a problem communicating with the database. 

        CommunicationError 
            There was a problem communicating with the remote service. 

    Remove-Item 
        HostingUnitObjectToDeleteDoesNotExist 
            The specified hosting unit object does not exist. 

        HypervisorConnectionObjectToDeleteDoesNotExist 
            The specified hypervisor connection object does not exist. 

        InputPathInvalid 
            The specified path is invalid because it is not in one of the following 
            formats: 

                XDHyp:\Connections\<Name> 
                XDHyp:\Connections\{Guid} 
                XDHyp:\HostingUnits\<Name> 
                XDHyp:\HostingUnits\{Guid} 

        HypervisorConnectionObjectToDeleteIsInUse 
            The specified hypervisor connection object cannot be deleted 
            because it is being used by one or more hosting units. 

        ExceptionThrown 
            An unexpected error occurred. 

        DatabaseError 
            There was a problem communicating with the database. 

        CommunicationError 
            There was a problem communicating with the remote service. 

        ObjectCannotBeRemoved 
            The specified object cannot be removed. 

    Rename-Item 
        InputPathInvalid 
            The specified path is invalid because it is not in one of the following 
            formats: 

                XDHyp:\Connections\<Name>  
                XDHyp:\Connections\{Guid} 
                XDHyp:\HostingUnits\<Name>  
                XDHyp:\HostingUnits\{Guid} 

        HostingUnitDuplicateNameExists 
            A hosting unit object with the same name already exists. Hosting 
            unit names must be unique. 

        HypervisorConnectionDuplicateNameExists 
            A hypervisor connection object with the same name already exists. 
            Hypervisor connection names must be unique. 

        InputNameInvalid 
            The new name specified for the hosting unit or hypervisor 
            connection is invalid because it contains one or more of the following 
            characters: \/;:#.*?=<>|[]()"'{}. 

        ExceptionThrown 
            An unexpected error occurred. 

        DatabaseError 
            There was a problem communicating with the database. 

        CommunicationError 
            There was a problem communicating with the remote service. 

    Set-Item 
        InputPathInvalid 
            The specified path is invalid because it is not in one of the following 
            formats: 

                XDHyp:\Connections\<Name> 
                XDHyp:\Connections\{Guid} 
                XDHyp:\HostingUnits\<Name> 
                XDHyp:\HostingUnits\{Guid} 

        HostingUnitObjectToUpdateDoesNotExist 
            The specified hosting unit object does not exist. 

        HostingUnitNetworkPathInvalid 
            The new network path specified for the hosting unit is invalid. 
            Either the network path does not exist or it is not relative to the 
            root path of the hosting unit. 

        HypervisorConnectionObjectToUpdateDoesNotExist 
            The specified hypervisor connection object does not exist. 

        ExceptionThrown 
            An unexpected error occurred. 

        DatabaseError 
            There was a problem communicating with the database. 

        DatabaseNotConfigured 
        The operation could not be completed because the database for the service 
        is not configured. 

        DataStoreException 
        An error occurred in the service while attempting a database operation. 
        Communication with the database failed for various reasons. 

        CommunicationError 
            There was a problem communicating with the remote service. 
