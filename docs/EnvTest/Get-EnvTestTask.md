# Get-EnvTestTask

   Gets one or more EnvTestTask(s)

## Syntax
```
Get-EnvTestTask [-TaskId <Guid>] [-List] [-AdminAddress <String>] [<CommonParameters>]
```

## Detailed Description
   Returns either the current task, a specified task, or list of tasks that are currently known to the EnvTest Service.

## Related Commands
  * [Get-EnvTestDefinition](Get-EnvTestDefinition/)
  * [Get-EnvTestSuiteDefinition](Get-EnvTestSuiteDefinition/)
  * [Start-EnvTestTask](Start-EnvTestTask/)
  * [Switch-EnvTestTask](Switch-EnvTestTask/)
  * [Stop-EnvTestTask](Stop-EnvTestTask/)
  * [Remove-EnvTestTask](Remove-EnvTestTask/)
  * [Add-EnvTestTaskMetadata](Add-EnvTestTaskMetadata/)
  * [Remove-EnvTestTaskMetadata](Remove-EnvTestTaskMetadata/)
## Parameters

| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| TaskId | Specifies the task identifier to be returned.  This value can be retrieved from an existing task's $task.TaskId property. | false | false |  |
| List | List all running tasks, including the current one. | false | false | false |
| AdminAddress | Specifies the address of a XenDesktop controller the PowerShell snap-in will connect to. You can provide this as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type
### 
   
## Return Values
### Citrix.EnvTest.Sdk.EnvTestTask
   A description of a previously started task.
## Examples

### EXAMPLE 1
```
$currentTask = Get-EnvTestTask
```
   Description<br>-----------<br>Retrieve the current task.  The current task is the most recently created task unless Switch-EnvTestTask explicitly changes it.
### EXAMPLE 2
```
$taskOfSpecificId = Get-EnvTestTask -TaskId 36C0EC52-2039-4D6E-B690-9F02F8CEFFCC
```
   Description<br>-----------<br>Retrieve a fresh copy of a task object based on a known task id, which is always a Guid.  This id can be retrieved from an existing task object via its $task.TaskId property.
### EXAMPLE 3
```
$allKnownTasks = Get-EnvTestTask -List
```
   Description<br>-----------<br>Retrieve the list of current tasks.  This list includes any task started by the Start-EnvTestTask cmdlet since the service started that has not later been removed via Remove-EnvTestTask.
