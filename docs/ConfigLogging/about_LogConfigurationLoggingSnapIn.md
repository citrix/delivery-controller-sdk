# about_LogConfigurationLoggingSnapIn
## TOPIC
    about_LogConfigurationLoggingSnapin 

## SHORT DESCRIPTION
   The Configuration Logging Service PowerShell snap-in provides administrative 
   functions for the Configuration Logging Service. 

## COMMAND PREFIX
    All commands in this snap-in have the noun prefixed with 'Log'. 

## LONG DESCRIPTION
    The Configuration Logging Service PowerShell snap-in enables both local 
    and remote administration of the Configuration Logging Service. 

    The Configuration Logging Service logs configuration changes or  
    administrator requested state changes made to the site. Configuration 
    Logging can be configured, site wide, to be mandatory or optional. If  
    mandatory logging is selected, then any attempts to change site  
    configuration or state when the logging mechanism is unavailable  
    are denied. 

    The Configuration Logging Service stores information about the logged 
    changes in a database which can be configured to be separate from  
    the site database. 

    The snap-in provides storage and configuration of these entities: 
     
    Site 
        The Configuration Logging Site object holds global settings which 
        control the behaviour of the Configuration Logging Service. The site 
        object can be configured by the Set-LogSite cmdlet. The properties of 
        the site object are returned by the Get-LogSite cmdlet. 

    High Level Operations 
        A high level operation object represents a logged configuration change  
        performed from Desktop Studio, Desktop Director or a PowerShell Script. 

        The XenDesktop consoles log high level operations when: 

          1) Executing operations which performs configuration changes. 
          2) Executing operations which performs administration related  
             activities which may affect site configuration. 
            
       PowerShell scripts which carry out customized configuration changes can 
       also log high level operations via cmdlets Start-LogHighLevelOperation  
       and Stop-LogHighLevelOperation. 
             
    Low Level Operations 
        A low level operation object represents a logged configuration change 
        performed by a service. One or more low level operation objects are  
        used to record the actions performed by a services in order to fulfil 
        a high level operation initiated from the consoles, or from PowerShell 
        scripts. 

        Low level operations in the system are returned by cmdlet  
        Get-LogLowLevelOperation. 
     
    Operation Details 
        A low level operation performed by a service can affect a number of  
        individual objects, or a number of properties on an object. An operation 
        detail log records each individual change to an object. This includes  
        the creation and deletion of the object, as well as changes to  
        individual properties of the object. 

        One or more operation detail objects are used to record specific changes to 
        each object that is affected by a low level service operation. 

        Operation details are included in the data returned from 
        the Get-LogLowLevelOperation cmdlet. 

    High Level Operations, Low Level Operations and Operation Details are  
    arranged in a hierarchy. A High Level Operation can have multiple 
    Low Level Operations, and each Low Level Operation can have multiple 
    Operation Details. 

    Setting up a separate logging database 
    -------------------------------------- 
    After creating the database on the database server, the logging database  
    can be setup and configured for use by:  
    
      1) Generating the database schema, and applying it the logging database 
      2) Configuring the configuration logging service to use the new logging database. 
    
    The logging database schema can be generated from the Get-LogDBSchem cmdlet, 
    as illustrated below: 
       Get-LogDBSchema -DatabaseName "loggingDB" 
                       -ServiceGroupName "service group name"  
                       -ScriptType Database  
                       -LocalDatabase:$LocalDB 
                       -DataStore Logging 

    The configuration logging service can be configured to use the logging  
    database with the Set-LogDBConnection cmdlet, as illustrated below: 
       Set-LogDBConnection -DataStore Logging -DBConnection $null 
       Set-LogDBConnection -DataStore Logging -DBConnection "new logging db connection string" 
        
    
   Configuration Logging site settings 
   ----------------------------------- 
    
   On the Site object: 
    
     o The 'State' setting allows configuration logging to be disabled, enabled, 
       or made mandatory.  
          
     o The 'Locale' setting specifies the language in which configuration 
       logging data text will be stored.  
        
   See Get-LogSite cmdlet help for further information on these settings. 
        
   This locale setting applies to the text description that is associated with 
   each log , e.g. ‘Create Catalog’. It  doesn't apply to other textual  
   information in the log like the names of parameters passed to  
   operations, e.g. ‘CatalogName’.  
     
   This localisation is applied when the data is logged, and not when the  
   logs are viewed later. For example, logs which are created in English 
   will be displayed in English on an end user system which may be configured 
   with a different locale. 
