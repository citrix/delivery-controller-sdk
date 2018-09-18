# Remove-EnvTestTask

   Removes from the database completed tasks for the EnvTest Service.

## Syntax
```
Remove-EnvTestTask [-TaskId <Guid>] [-AdminAddress <String>] [<CommonParameters>]

Remove-EnvTestTask [-Task <EnvTestTask>] [-AdminAddress <String>] [<CommonParameters>]
```

## Detailed Description
   Enables completed tasks that have run within the EnvTest Service to be removed from the database.

## Related Commands
  * [Get-EnvTestDefinition](Get-EnvTestDefinition/)
  * [Get-EnvTestSuiteDefinition](Get-EnvTestSuiteDefinition/)
  * [Get-EnvTestTask](Get-EnvTestTask/)
  * [Start-EnvTestTask](Start-EnvTestTask/)
  * [Switch-EnvTestTask](Switch-EnvTestTask/)
  * [Stop-EnvTestTask](Stop-EnvTestTask/)
  * [Add-EnvTestTaskMetadata](Add-EnvTestTaskMetadata/)
  * [Remove-EnvTestTaskMetadata](Remove-EnvTestTaskMetadata/)
## Parameters

| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| TaskId | Specifies the identifier of the task to be removed, retrieveable from the $task.TaskId property. | false | false |  |
| Task | Specifies the task to be removed. | false | true (ByValue) |  |
| AdminAddress | Specifies the address of a XenDesktop controller the PowerShell snap-in will connect to. You can provide this as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type
### 
   
## Return Values
### 
   
## Examples

### EXAMPLE 1
```
Remove-EnvTestTask
```
   Description<br>-----------<br>Removes the current task from the EnvTest service.
### EXAMPLE 2
```
Remove-EnvTestTask -TaskId 50A4139F-2B55-4A97-A1BE-20EE4E124AA3
```
   Description<br>-----------<br>Removes a task from the EnvTest service via its id, which is available from an existing task's $task.TaskId property.
### EXAMPLE 3
```
$secondTask = $(Get-EnvTestTask -List)[1]
Remove-EnvTestTask -Task $secondTask
```
   Description<br>-----------<br>Removes the second task in the list returned by Get-EnvTestTask -List.
