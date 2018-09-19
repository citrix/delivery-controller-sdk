# Stop-EnvTestTask

   Stops a still running task from completing.

## Syntax
```
Stop-EnvTestTask [-TaskId <Guid>] [-AdminAddress <String>] [<CommonParameters>]

Stop-EnvTestTask [-Task <EnvTestTask>] [-AdminAddress <String>] [<CommonParameters>]
```

## Detailed Description
   Stops a still running task from completing.  A task may still be retreived via Get-EnvTestTask until it Remove-EnvTestTask is called with its task id.

## Related Commands
  * [Get-EnvTestDefinition](Get-EnvTestDefinition/)
  * [Get-EnvTestSuiteDefinition](Get-EnvTestSuiteDefinition/)
  * [Get-EnvTestTask](Get-EnvTestTask/)
  * [New-EnvTestTask](New-EnvTestTask/)
  * [Start-EnvTestTask](Start-EnvTestTask/)
  * [Switch-EnvTestTask](Switch-EnvTestTask/)
  * [Remove-EnvTestTask](Remove-EnvTestTask/)
  * [Add-EnvTestTaskMetadata](Add-EnvTestTaskMetadata/)
  * [Remove-EnvTestTaskMetadata](Remove-EnvTestTaskMetadata/)
## Parameters

| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| TaskId | The id of the task to stop, retrieveable from the $task.TaskId property. | false | false |  |
| Task | An EnvTestTask representing the task to stop | false | true (ByValue) |  |
| AdminAddress | Specifies the address of a XenDesktop controller the PowerShell snap-in will connect to. You can provide this as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type
### 
   
## Return Values
### 
   
## Examples

### EXAMPLE 1
```
Stop-EnvTestTask
```
   Description<br>-----------<br>Stops the current task from completing if it is still running.
### EXAMPLE 2
```
Stop-EnvTestTask -TestId 50A4139F-2B55-4A97-A1BE-20EE4E124AA3
```
   Description<br>-----------<br>Stops a task from completing via its id, which is available from an existing task's $task.TaskId property.
### EXAMPLE 3
```
$secondTask = $(Get-EnvTestTask -List)[1]
Stop-EnvTestTask -Task $secondTask
```
   Description<br>-----------<br>Stops the second task in the list returned by Get-EnvTestTask -List.
