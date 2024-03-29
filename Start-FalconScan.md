# Start-FalconScan
## SYNOPSIS
Start an on-demand scan
## DESCRIPTION
Requires 'On-demand scans (ODS): Write'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
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
|Notification|Boolean|||||||
|MaxDuration|Int32|Allowable scan duration, in hours|`0`|`24`||||
|PauseDuration|Int32|Allowable pause duration, in hours|`0`|`24`||||
|Description|String|On-demand scan description||||||
|GroupId|String[]|Host Group identifier||||||
|Id|String[]|Host identifier||||X|X|
## SYNTAX
```powershell
Start-FalconScan [-FilePath] <String[]> [-SensorDetection] <String> [-SensorPrevention] <String> [-CloudDetection] <String> [-CloudPrevention] <String> [[-ScanExclusion] <String[]>] [[-ScanInclusion] <String[]>] [[-Quarantine] <Boolean>] [[-MaxFileSize] <Int32>] [[-CpuPriority] <String>] [[-Notification] <Boolean>] [[-MaxDuration] <Int32>] [[-PauseDuration] <Int32>] [[-Description] <String>] [-GroupId <String[]>] [-Id <String[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
POST /ods/entities/scans/v1
```
### falconpy
[create_scan](https://github.com/CrowdStrike/falconpy/wiki/ods#create_scan)
## USAGE

_2023-11-27: PSFalcon v2.2.6_
