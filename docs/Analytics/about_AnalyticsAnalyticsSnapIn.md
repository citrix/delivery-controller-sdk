# about_AnalyticsAnalyticsSnapIn
## TOPIC
    about_AnalyticsAnalyticsSnapin 

## SHORT DESCRIPTION
   The Analytics PowerShall snap-in provides administrative functions for the Analytics Service. 

## COMMAND PREFIX
    All commands in this snap-in have the noun prefixed with 'Analytics'. 

## LONG DESCRIPTION
    The Analytics Service PowerShell snap-in enables both local and remote administration of the 
    Analytics Service. 

    The Analytics Service collects Citrix CEIP data about the DDC. For more information about CEIP, 
    see http://more.citrix.com/XD-CEIP. 

    This snap-in provides commands for a Citrix administrator to enable a data collection, import 
    the collection data points file, and query the current status of the Analytics database 
    configuration and service. 

    For more information on the Analytics Service, see the help topic about Analytics Service. 

    Use the command 'Get-Command -Module Citrix.Analytics.Admin.V1' to see a complete list of 
    commands supported by this snap-in. 

    For usage of each command, use the Get-Help command to display the help text for each command. 

    In addition to pre-programed schedules hard-coded in the Analytics Service, administrators can 
    use the Set-AnalyticsSite command to trigger immediate data collection and upload. The registry 
    string value HKLM/Software/Citrix/XDServices/Analytics/DoOperation can be specified to indicate 
    the type of collection to be performed upon the execution of the Set-AnalyticsSite command. If 
    the data stored in this registry value is set to 'Collect', then upon issuance of the command 
    'Set-AnalyticsSite -Enabled $true', the Analytics Service starts a collection immediately. The 
    result of the collection is a .zip file, whose location is stored in the the registry value 
    'DoOperationResult'. The collected result is not uploaded to the Citrix CEIP site. 

    If the value of 'DoOperation' is 'CollectAndUpload', then a collection is performed and the 
    result is also uploaded to the Citrix CEIP site. 

    If the value of 'DoOperation' is 'CollectSite', then only site data is collected. For detailed 
    list of site data, refer to the 'Scope' parameter for each data point in the DataPoints.xml 
    file, which can be found under c:\Program Files\Citrix\XenDesktopPoshSDK\Module\ 
    Citrix.XenDesktop.Admin.V1\Citrix.XenDesktop.Admin. 

    If the value of 'DoOperation' is 'CollectHost', then only host data is collected, as specified 
    in the data points file. 

    The data points file can be imported using the Import-AnalyticsDataDefinition file. The file 
    must be a file signed by Citrix. 

    When running, the Analytics Service periodically collects data using the latest data point file 
    stored in the DDC database. The collection runs at approximately every 30 minutes to perform 
    data collection. Each collection runs for 5 to 10 minutes, depending on the size of data to 
    be collected. The service has been optimized so that minimal system resources are used to do 
    the data collection. 

    If collection results are not uploaded immediately, they can be manually uploaded. If they are 
    not manually uploaded, they will be periodically packaged and uploaded by the Analytics Service. 
    If for any reason an upload fails, the Service will try again but not before doubling the amount 
    of time between the most recent to successful uploads. If upload keeps failing, very soon the 
    Service will wait a very long time to attempt the next upload. The time can be weeks or months. 
    A system reboot resets the upload wait time. 

    The collection and upload algorithm and schedules are hard-coded in the Service and cannot be 
    changed. 
