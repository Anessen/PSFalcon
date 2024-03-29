# Edit-FalconFileVantageRule
## SYNOPSIS
Modify a rule within a FileVantage rule group
## DESCRIPTION
Requires 'Falcon FileVantage: Write'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Id|String|Rule identifier||||X|X|
|Precedence|Int32|Precedence of the rule inside of the existing rule group|||||X|
|Path|String|Path of the directory, file, or registry key to monitor|`1`|`250`|||X|
|Depth|String|Monitoring depth below the initial target directory/file/registry key|||`1`<BR>`2`<BR>`3`<BR>`4`<BR>`5`<BR>`ANY`||X|
|Severity|String|Rule severity|||`Low`<BR>`Medium`<BR>`High`<BR>`Critical`||X|
|Description|String|Rule description||`500`|||X|
|Include|String|User<BR>Restrict monitoring to changes made by one or more users|||||X|
|Exclude|String|User<BR>Exclude changes made by one or more users|||||X|
|IncludeProcess|String|Restrict monitoring to changes made by one or more processes|||||X|
|ExcludeProcess|String|Exclude changes made by one or more processes|||||X|
|IncludeUser|String|Restrict monitoring to changes made by one or more users|||||X|
|ExcludeUser|String|Exclude changes made by one or more users|||||X|
|DirectoryAttribute|Boolean|Track directory attribute change events|||||X|
|DirectoryCreate|Boolean|Track directory create events|||||X|
|DirectoryDelete|Boolean|Track directory delete events|||||X|
|DirectoryPermission|Boolean|Track directory permission change events|||||X|
|DirectoryRename|Boolean|Track directory rename events|||||X|
|FileAttribute|Boolean|Track file attribute change events|||||X|
|FileChange|Boolean|Track file change events|||||X|
|FileDelete|Boolean|Track file delete events|||||X|
|FilePermission|Boolean|Track file permission change events|||||X|
|FileRename|Boolean|Track file rename events|||||X|
|FileWrite|Boolean|Track file write events|||||X|
|RegKeyCreate|Boolean|Track registry key create events|||||X|
|RegKeyDelete|Boolean|Track registry key delete events|||||X|
|RegKeyRename|Boolean|Track registry key rename events|||||X|
|RegKeySet|Boolean|Track registry key set events|||||X|
|RegValueCreate|Boolean|Track registry value create events|||||X|
|RegValueDelete|Boolean|Track registry value delete events|||||X|
|EnableContentCapture|Boolean|Enable the capture of file content during events|||||X|
|ContentFiles|String[]|A specific list of files to monitor for content changes|||||X|
|RuleGroupId|String|FileVantage rule group identifier|||||X|
## SYNTAX
```powershell
Edit-FalconFileVantageRule [-Id] <String> [-Precedence] <Int32> [[-Path] <String>] [[-Depth] <String>] [[-Severity] <String>] [[-Description] <String>] [[-Include] <String>] [[-Exclude] <String>] [[-IncludeProcess] <String>] [[-ExcludeProcess] <String>] [[-IncludeUser] <String>] [[-ExcludeUser] <String>] [[-DirectoryAttribute] <Boolean>] [[-DirectoryCreate] <Boolean>] [[-DirectoryDelete] <Boolean>] [[-DirectoryPermission] <Boolean>] [[-DirectoryRename] <Boolean>] [[-FileAttribute] <Boolean>] [[-FileChange] <Boolean>] [[-FileDelete] <Boolean>] [[-FilePermission] <Boolean>] [[-FileRename] <Boolean>] [[-FileWrite] <Boolean>] [[-RegKeyCreate] <Boolean>] [[-RegKeyDelete] <Boolean>] [[-RegKeyRename] <Boolean>] [[-RegKeySet] <Boolean>] [[-RegValueCreate] <Boolean>] [[-RegValueDelete] <Boolean>] [[-EnableContentCapture] <Boolean>] [[-ContentFiles] <String[]>] -RuleGroupId <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
PATCH /filevantage/entities/rule-groups-rules/v1
```
### falconpy
[updateRules](https://github.com/CrowdStrike/falconpy/wiki/filevantage#updateRules)
## USAGE

_2023-11-27: PSFalcon v2.2.6_
