# New-FalconFileVantageExclusion
## SYNOPSIS
Create a scheduled exclusion within a FileVantage policy
## DESCRIPTION
Requires 'Falcon FileVantage: Write'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Name|String|Scheduled exclusion name|`1`|`100`|||X|
|ScheduleStart|String|Start of scheduled exclusion (RFC3339)|||||X|
|ScheduleEnd|String|End of scheduled exclusion (RFC3339)|||||X|
|Timezone|String|Timezone for scheduled start/end time (TZ database format)|||||X|
|Repeated|Object|Object containing properties for repeating exclusion based on scheduled start/end time ('all_day', 'end_time',<BR>'frequency', 'monthly_days', 'occurrence', 'start_time', and 'weekly_days')|||||X|
|Process|String|One or more process names in glob syntax, separated by commas||`500`|||X|
|User|String|One or more user names in glob syntax, separated by commas||`500`|||X|
|Description|String|Scheduled exclusion description||`500`|||X|
|PolicyId|String|FileVantage policy identifier|||||X|
## SYNTAX
```powershell
New-FalconFileVantageExclusion [-Name] <String> [-ScheduleStart] <String> [[-ScheduleEnd] <String>] [[-Timezone] <String>] [[-Repeated] <Object>] [[-Process] <String>] [[-User] <String>] [[-Description] <String>] [-PolicyId] <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
POST /filevantage/entities/policy-scheduled-exclusions/v1
```
### falconpy
[createScheduledExclusions](https://github.com/CrowdStrike/falconpy/wiki/filevantage#createScheduledExclusions)
## USAGE

_2023-11-27: PSFalcon v2.2.6_
