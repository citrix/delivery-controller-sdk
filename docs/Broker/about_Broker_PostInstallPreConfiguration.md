
# about\_Broker\_PostInstallPreConfiguration

## Topic
Citrix Broker SDK - Post-Installation Configuration


## Short Description
Describes how to configure the Citrix Broker Service port numbers, URL reservations, and Windows Firewall exclusions.


## Long Description
The XenDesktop installer configures the Citrix Broker Service with information specified during the installation. To change that configuration, use the BrokerService.exe command-line tool on each controller you want to change.

The default installation location of BrokerService.exe is:

%ProgramFiles%\\Citrix\\Broker\\Service\\BrokerService.exe

BrokerService.exe supports the following optional command-line parameters:

-SdkPort &lt;port&gt;  (default 80) Configures the port on which the broker listens for requests from SDK cmdlets. If you change this default value, specify the new value in the AdminAddress parameter on broker cmdlets. For example, if you changed the port to 8080, specify it as follows:

Get-BrokerSite -AdminAddress localhost:8080

-VdaPort &lt;port&gt;  (default 80) Configures the port on which the broker listens for registration requests from broker machines.

-WiPort &lt;port&gt;  (default 80) Configures the port on which the broker listens for XML requests from StoreFront/Web Interface.

-WiSslPort &lt;port&gt;  (default 443) Configures the port on which the broker listens for SSL (Secure Socket Layer) XML requests from StoreFront/Web Interface.

-ConfigureFirewall Configures Windows Firewall exclusions for the specified ports.

-Show Shows the current configuration settings.

-Uninstall Removes configuration settings, including Windows Firewall exclusions and URL reservations.

-LogFile &lt;fileName&gt; Configures the file location for logging to a text file. The directory containing the log file must grant write access to the NetworkService account.

-Upgrade Performs configurations required after an upgrade.

-Quiet Suppresses console output for status messages.

-? or -Help Shows usage information for the command.


