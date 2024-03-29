# New-FalconScheduledScan
## SYNOPSIS
Create a scheduled scan targeting host groups
## DESCRIPTION
Requires 'On-demand scans (ODS): Write'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|StartTime|String|Start time (yyyy-MM-ddThh:mm)||||||
|Repeat|String|Repetition frequency|||`never`<BR>`daily`<BR>`weekly`<BR>`every_other_week`<BR>`every_4_weeks`<BR>`monthly`|||
|FilePath|String[]|File path(s) to scan||||||
|SensorDetection|String|On-sensor machine-learning detection level|||`disabled`<BR>`cautious`<BR>`moderate`<BR>`aggressive`<BR>`extra_aggressive`|||
|SensorPrevention|String|On-sensor machine-learning prevention level|||`disabled`<BR>`cautious`<BR>`moderate`<BR>`aggressive`<BR>`extra_aggressive`|||
|CloudDetection|String|Cloud-based machine-learning detection level|||`disabled`<BR>`cautious`<BR>`moderate`<BR>`aggressive`<BR>`extra_aggressive`|||
|CloudPrevention|String|Cloud-based machine-learning prevention level|||`disabled`<BR>`cautious`<BR>`moderate`<BR>`aggressive`<BR>`extra_aggressive`|||
|ScanExclusion|String[]|File path(s) to exclude, in glob syntax||||||
|ScanInclusion|String[]|File path(s) to include, in glob syntax||||||
|Quarantine|Boolean|Quarantine malicious files||||||
|MaxFileSize|Int32|Maximum file size, in MB||||||
|CpuPriority|String|Maximum CPU utilization|||`up_to_1`<BR>`up_to_25`<BR>`up_to_50`<BR>`up_to_75`<BR>`up_to_100`|||
|Notification|Boolean|Show notification to end user||||||
|MaxDuration|Int32|Allowable scan duration, in hours|`0`|`24`||||
|PauseDuration|Int32|Allowable pause duration, in hours|`0`|`24`||||
|Description|String|On-demand scan description||||||
|Id|String[]|Host group identifier||||X|X|
## SYNTAX
```powershell
New-FalconScheduledScan [-StartTime] <String> [-Repeat] <String> [-FilePath] <String[]> [-SensorDetection] <String> [-SensorPrevention] <String> [-CloudDetection] <String> [-CloudPrevention] <String> [[-ScanExclusion] <String[]>] [[-ScanInclusion] <String[]>] [[-Quarantine] <Boolean>] [[-MaxFileSize] <Int32>] [[-CpuPriority] <String>] [[-Notification] <Boolean>] [[-MaxDuration] <Int32>] [[-PauseDuration] <Int32>] [[-Description] <String>] [-Id] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
POST /ods/entities/scheduled-scans/v1
```
### falconpy
[schedule_scan](https://github.com/CrowdStrike/falconpy/wiki/ods#schedule_scan)
## USAGE

_2023-11-27: PSFalcon v2.2.6_
