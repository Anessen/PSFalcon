# Receive-FalconRule
## SYNOPSIS
Download the most recent ruleset, or a specific ruleset
## DESCRIPTION
Requires 'Rules (Falcon Intelligence): Read'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Type|String|Ruleset type, used to retrieve the latest ruleset|||`common-event-format`<BR>`netwitness`<BR>`snort-suricata-changelog`<BR>`snort-suricata-master`<BR>`snort-suricata-update`<BR>`yara-changelog`<BR>`yara-master`<BR>`yara-update`|||
|IfNoneMatch|String|Download the latest rule set only if it doesn't a matching 'tags' value||||||
|IfModifiedSince|String|Restrict results to those modified after a provided date (HTTP, ANSIC or RFC850 format)||||||
|Path|String|Destination path||||||
|Id|Int32|Ruleset identifier, used for a specific ruleset||||X|X|
|Force|Switch|Overwrite an existing file when present||||||
## SYNTAX
```powershell
Receive-FalconRule [-Path] <String> [-Id] <Int32> [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```
```powershell
Receive-FalconRule [-Type] <String> [[-IfNoneMatch] <String>] [[-IfModifiedSince] <String>] [-Path] <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
GET /intel/entities/rules-files/v1
GET /intel/entities/rules-latest-files/v1
```
### falconpy
[GetIntelRuleFile](https://github.com/CrowdStrike/falconpy/wiki/intel#GetIntelRuleFile)<BR>[GetLatestIntelRuleFile](https://github.com/CrowdStrike/falconpy/wiki/intel#GetLatestIntelRuleFile)
## USAGE
### Download the latest rule set
```powershell
Receive-FalconRule -Type yara-master -Path .\yara-master.zip
```
### Download a specific rule set
```powershell
Receive-FalconRule -Id <id> -Path .ules.zip
```

_2023-11-27: PSFalcon v2.2.6_
