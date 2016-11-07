# Test-ConfigServiceInstanceAvailability

   Tests whether the supplied service instances are responding to requests.

## Syntax
```
Test-ConfigServiceInstanceAvailability [-ServiceInstance] <ServiceInstance[]> [-MaxDelaySeconds <Int32>] [-ForceWaitForOneOfEachType] [-AdminAddress <String>] [<CommonParameters>]
```

## Detailed Description
   

## Related Commands
  * [Register-ConfigServiceInstance](Register-ConfigServiceInstance.html)
  * [Unregister-ConfigRegisteredServiceInstance](Unregister-ConfigRegisteredServiceInstance.html)
  * [Get-ConfigRegisteredServiceInstance](Get-ConfigRegisteredServiceInstance.html)
## Parameters

| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| ServiceInstance | The service instances to test. | true | true (ByValue) |  |
| MaxDelaySeconds | The timeout period to wait before concluding that services are unresponsive. | false | false | Infinite |
| ForceWaitForOneOfEachType | If at least one of each type of service responds, finish immediately. | false | false |  |
| AdminAddress | Specifies the host name or IP address of the controller to which the PowerShell snap-in connects. | false | false | 'LocalHost'.  Once a value is specified by any command, this value becomes the new default. |

## Input Type
### 
   
## Return Values
### System.Management.Automation.PSObject<br>    This represents a service instance and has the following parameters;<br>    ServiceGroupUid <Guid><br>        The unique identifer for the service group to which the service instance belongs.<br>    ServiceGroupName <string><br>        The name of the service group that the service instance is part of.<br>    ServiceInstanceUid <Guid><br>        The unique identifier for the service instance.<br>    ServiceType <string><br>        The type of the service group.<br>    Address <string><br>        The contact address for the service instance.<br>    Binding <string><br>        The binding to use for connections to the service instance.<br>    Version <int><br>        The version of the service instance.<br>    ServiceAccount <string><br>        The AD computer account for the computer that is providing the service instance.<br>    ServiceAccountSid <string><br>        The AD computer account SID for the computer that is providing the service instance.<br>    InterfaceType <string><br>        The interface type for the service instance.<br>    Metadata <Citrix.Configuration.Sdk.Metadata[]><br>        The metadata for the service instance.<br>    Status <Citrix.Configuration.Sdk.Commands.Availability><br>        An enumeration value indicating whether the service is Responding, NotResponding, Unknown, or BadBindingType.<br>    ResponseTime <System.TineSpan><br>        The interval elapsed between hailing the service and getting a definite response
   ## Notes
   The Availability Status Codes are o Responding: Got a positive response o NotResponding: Got a response, but it was negative or the connection was refused o Unknown: Did not respond in time / timed-out o BadBindingType: Binding parameter in ServiceInstance is not wcf_HTTP_kerb
## Examples

### EXAMPLE 1
```
C:\>Get-ConfigRegisteredServiceInstance | Test-ConfigServiceInstanceAvailability -ForceWaitForOneOfEachType
```
   Description<br>-----------<br>Test all the service instances that are registered in the Configuration Service, returning when one of each type is responding.
### EXAMPLE 2
```
C:\>Test-ConfigServiceInstanceAvailability -ServiceInstance $services -MaxDelaySeconds 5
```
   Description<br>-----------<br>Test each of the given services, allowing a 5 second time-out.
