
# Get-Userprofiledefinition
Gets the high level description of a configuration for profile management, based on a byte array (blob).
## Syntax
```
Get-UserProfileDefinition [-ByteArray] <Byte[]> [-ExcludeUnconfigured] [<CommonParameters>]
```
## Detailed Description
Use this command to convert a configuration byte array into a set of named property settings. The byte array will either have been retrieved from the Broker, or from the New-UserProfileConfiguration cmdlet.


## Related Commands

## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| ByteArray | Specifies the low-level byte array (blob) to be interpreted. | true | true (ByValue) |  |
| ExcludeUnconfigured | When this switch is supplied, the returned object will only carry the properties whose values have been explicitly set. Properties whose values are unconfigured will be omitted. When this switch is not supplied, the full set of configuration properties will be returned, and any unconfigured settings will just appear to be set to their default value. | false | false |  |

## Input Type

### Byte\[\]
The cmdlet accepts the ByteArray parameter as pipeline input.
## Return Values

### System.Management.Automation.Psobject
This cmdlet outputs a single PSObject with multiple properties. Each property denotes one setting within the configuration set. The following is a summary of the properties and their data types:<br>ServiceActive  (bool?)<br>ProcessedGroups  (string\[\])<br>ExcludedGroups  (string\[\])<br>ProcessAdmins  (bool?)<br>UserStorePath  (string)<br>PSMidSessionWriteBack  (bool?)<br>OfflineSupport  (bool?)<br>DeleteCachedProfilesOnLogoff  (bool?)<br>ProfileDeleteDelay  (int?)<br>MigrateWindowsProfilesToUserStore  (MigrateWindowsProfilesToUserStoreEnum?)<br>LocalProfileConflictHandling  (LocalProfileConflictHandlingEnum?)<br>TemplateProfilePath  (string)<br>TemplateProfileOverridesLocalProfile  (bool?)<br>TemplateProfileOverridesRoamingProfile  (bool?)<br>TemplateProfileIsMandatory  (bool?)<br>LoadRetries  (int?)<br>ProcessCookieFiles  (bool?)<br>DisableDynamicConfig  (bool?)<br>LogoffRatherThanTempProfile  (bool?)<br>DebugMode  (bool?)<br>LogLevel\_Warnings  (bool?)<br>LogLevel\_Information  (bool?)<br>LogLevel\_FileSystemNotification  (bool?)<br>LogLevel\_FileSystemActions  (bool?)<br>LogLevel\_RegistryActions  (bool?)<br>LogLevel\_RegistryDifference  (bool?)<br>LogLevel\_ActiveDirectoryActions  (bool?)<br>LogLevel\_PolicyUserLogon  (bool?)<br>LogLevel\_Logon  (bool?)<br>LogLevel\_Logoff  (bool?)<br>LogLevel\_UserName  (bool?)<br>MaxLogSize  (int?)<br>DebugFilePath  (string)<br>ExclusionList  (string\[\])<br>IncludeListRegistry  (string\[\])<br>ExclusionListSyncFiles  (string\[\])<br>ExclusionListSyncDir  (string\[\])<br>SyncDirList  (string\[\])<br>SyncFileList  (string\[\])<br>MirrorFoldersList  (string\[\])<br>PSEnabled  (bool?)<br>PSAlwaysCache\_Enabled  (bool?)<br>PSAlwaysCache  (int?)<br>PSPendingLockTimeout  (int?)<br>PSUserGroups  (string\[\])<br>CPEnable  (bool?)<br>CPUserGroups  (string\[\])<br>CPSchemaPathData  (string)<br>CPPathData  (string)<br>CPMigrationFromBaseProfileToCPStore  (bool?)<br>FRAdminAccess  (bool?)<br>FRIncDomainName  (bool?)<br>FRAppDataEnabled  (FRAppDataEnum?)<br>FRAppDataPath  (string)<br>FRDesktopEnabled  (FRDesktopEnum?)<br>FRDesktopPath  (string)<br>FRStartMenuEnabled  (FRStartMenuEnum?)<br>FRStartMenuPath  (string)<br>FRDocumentsEnabled  (FRDocumentsEnum?)<br>FRDocumentsPath  (string)<br>FRPicturesEnabled  (FRPicturesEnum?)<br>FRPicturesPath  (string)<br>FRMusicEnabled  (FRMusicEnum?)<br>FRMusicPath  (string)<br>FRVideosEnabled  (FRVideosEnum?)<br>FRVideosPath  (string)<br>FRFavoritesEnabled  (FRFavoritesEnum?)<br>FRFavoritesPath  (string)<br>FRContactsEnabled  (FRContactsEnum?)<br>FRContactsPath  (string)<br>FRDownloadsEnabled  (FRDownloadsEnum?)<br>FRDownloadsPath  (string)<br>FRLinksEnabled  (FRLinksEnum?)<br>FRLinksPath  (string)<br>FRSearchesEnabled  (FRSearchesEnum?)<br>FRSearchesPath  (string)<br>FRSavedGamesEnabled  (FRSavedGamesEnum?)<br>FRSavedGamesPath  (string)
## Examples

### Example 1
```
C:\PS> $blob = New-UserProfileConfiguration

C:\PS>Get-UserProfileDefinition -ByteArray $blob
```
#### Description
The first command creates a fresh configuration set in its default state, and stores it in a Windows PowerShell variable. The second command interprets the new blob, and would output the individual properties of the default configuration.
### Example 2
```
C:\PS> New-UserProfileConfiguration | Get-UserProfileDefinition
```
#### Description
This command creates a fresh configuration set in its default state, and pipes the resulting byte array through to Get-UserProfileDefinition, which will interpret it and output its individual properties.
