# about_ConfigConfigurationSnapIn
## TOPIC
    about_ConfigConfigurationSnapin 

## SHORT DESCRIPTION
    The Configuration service PowerShell snap-in provides administrative 
    functions for the Configuration service. 

## COMMAND PREFIX
    All commands in this snap-in have the noun prefixed with 'Config'. 

## LONG DESCRIPTION
    The Configuration service PowerShell snap-in enables both local and remote 
    administration of the Configuration service.  It provides facilities to 
    store details about other services that are used in the XenDesktop 
    deployment. 

    All the services in the XenDesktop deployment use the Configuration service 
    as a directory to locate other services with which they need to 
    communicate.  The directory publishes a list of all the services, the  
    communication types they accept, and the facilities they offer. 

    The snap-in provides the following main entities: 

    Site Metadata 
        Metadata for the entire XenDesktop deployment.  This metadata is not  
        used directly by any of the XenDesktop services, but can be used by 
        third parties to store information for other purposes. 

    Registered Service Instances 
        Service instance items that have been retrieved from the available 
        services in the XenDesktop deployment and held in a directory in the 
        Configuration service.  Each physical service can host a collection of 
        service instances to provide different facilities. 

    Service Groups 
        A collection of service instances that are considered equivalent. 
        Service instances that are registered in the same service group provide 
        the same state and offer the same functionality. 

        Only one service group of each type is supported.  For example, there 
        must not be more than one service group with a ServiceType of 'Config'. 

    Site and Features 
        The configuration site is a top-level, logical representation of the  
        XenDesktop site, from the perspective of the configuration services  
        running within the site. 
