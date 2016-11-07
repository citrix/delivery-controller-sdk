# Switch-EnvTestTask

   Sets the current task that will be returned by a call to Get-EnvTestTask with no parameters.

## Syntax
```
Switch-EnvTestTask [-TaskId <Guid>] [-AdminAddress <String>] [<CommonParameters>]

Switch-EnvTestTask [-Task <EnvTestTask>] [-AdminAddress <String>] [<CommonParameters>]
```

## Detailed Description
   Sets the current task that will be returned by a call to Get-EnvTestTask with no parameters.

## Related Commands
  * [Get-EnvTestDefinition](Get-EnvTestDefinition.html)
  * [Get-EnvTestSuiteDefinition](Get-EnvTestSuiteDefinition.html)
  * [Get-EnvTestTask](Get-EnvTestTask.html)
  * [New-EnvTestTask](New-EnvTestTask.html)
  * [Start-EnvTestTask](Start-EnvTestTask.html)
  * [Stop-EnvTestTask](Stop-EnvTestTask.html)
  * [Remove-EnvTestTask](Remove-EnvTestTask.html)
  * [Add-EnvTestTaskMetadata](Add-EnvTestTaskMetadata.html)
  * [Remove-EnvTestTaskMetadata](Remove-EnvTestTaskMetadata.html)
## Parameters

| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| TaskId | Specifies the identifier of the task to be made current. | false | false |  |
| Task | The task object to be made current, retrieveable from the $task.TaskId property. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller the PowerShell snap-in will connect to. You can provide this as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type
### System.Management.Automation.PSObject
   Objects containing the TaskId parameter can be piped to the Remove-EnvTestTask command.
## Return Values
### 
   
## Examples

### EXAMPLE 1
```
Switch-EnvTestTask -TaskId 50A4139F-2B55-4A97-A1BE-20EE4E124AA3
```
   Description<br>-----------<br>Switches the current task to another via its id, which is available from an existing task's $task.TaskId property.
### EXAMPLE 2
```
$secondTask = $(Get-EnvTestTask -List)[1]          
Switch-EnvTestTask -Task $switchTask
```
   Description<br>-----------<br>Switches the current task to the second in the list returned by Get-EnvTestTask -List.
