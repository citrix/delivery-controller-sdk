# about_ProvMachineCreationSnapIn
## TOPIC
    about_ProvMachineCreationSnapin 

## SHORT DESCRIPTION
    The Machine Creation Service PowerShell snap-in provides administrative 
    functions for the Machine Creation Service. 

## COMMAND PREFIX
    All commands in this snap-in have the noun prefixed with 'Prov'. 

## LONG DESCRIPTION
    The Machine Creation Service PowerShell snap-in enables both local and 
    remote administration of the Machine Creation Service.  It provides 
    facilities to create virtual machines and manage the associated disk 
    images. 

    The snap-in provides two main entities: 

    Provisioning Scheme 
        Specifies details of new virtual machines created by the Machine 
        Creation Service.  Provisioning schemes define the following 
        information. 

        Hosting Unit 
            Provides details of the hypervisor and storage on which new virtual 
            machines will be created.  Stored and maintained by the Host 
            Service and PowerShell snap-in. 

        Identity Pool 
            Lists the Active Directory computer accounts available for use by 
            new virtual machines.  Stored and maintained by the Active Directory 
            Identity Service and PowerShell snap-in. 

        Master Image 
            Specifies the disk image that will be used for new virtual 
            machines.  Accessed through the hosting provider in the Host Service 
            snap-in. 

    Provisioned VM 
        Defines the virtual machines created by the Machine Creation Services. 
        These virtual machines are associated with the provisioning scheme from 
        which they were created. 

    The processes of creating provisioning schemes and new virtual machines can 
    take a significant amount of time to complete.  For this reason, these 
    long-running tasks can be run asynchronously so that other commands are 
    accessible while the processes are running.  Note, however, that only one 
    long-running task can operate on a provisioning scheme at any one time. 
    The processes are monitored using the Get-ProvTask command.  For more 
    information, see the help for Get-ProvTask. 
