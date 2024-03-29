# Invoke-FalconMalQuery
## SYNOPSIS
Initiate a Falcon MalQuery YARA hunt, exact search or fuzzy search
## DESCRIPTION
Requires 'MalQuery: Write'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|YaraRule|String|Schedule a YARA-based search||||||
|Type|String|Search pattern type|||`hex`<BR>`ascii`<BR>`wide`|||
|Value|String|Search pattern value||||||
|FilterFiletype|String[]|File type to include with the result|||`cdf`<BR>`cdfv2`<BR>`cjava`<BR>`dalvik`<BR>`doc`<BR>`docx`<BR>`elf32`<BR>`elf64`<BR>`email`<BR>`html`<BR>`hwp`<BR>`java.arc`<BR>`lnk`<BR>`macho`<BR>`pcap`<BR>`pdf`<BR>`pe32`<BR>`pe64`<BR>`perl`<BR>`ppt`<BR>`pptx`<BR>`python`<BR>`pythonc`<BR>`rtf`<BR>`swf`<BR>`text`<BR>`xls`<BR>`xlsx`|||
|FilterMeta|String[]|Subset of metadata fields to include in the result|||`sha256`<BR>`md5`<BR>`type`<BR>`size`<BR>`first_seen`<BR>`label`<BR>`family`|||
|MinSize|String|Minimum file size specified in bytes or multiples of KB/MB/GB||||||
|MaxSize|String|Maximum file size specified in bytes or multiples of KB/MB/GB||||||
|MinDate|String|Limit results to files first seen after this date||||||
|MaxDate|String|Limit results to files first seen before this date||||||
|Limit|Int32|Maximum number of results per request||||||
|Fuzzy|Switch|Search MalQuery quickly but with more potential for false positives||||||
## SYNTAX
```powershell
Invoke-FalconMalQuery [-Type] <String> [-Value] <String> [[-FilterFiletype] <String[]>] [[-FilterMeta] <String[]>] [[-MinSize] <String>] [[-MaxSize] <String>] [[-MinDate] <String>] [[-MaxDate] <String>] [[-Limit] <Int32>] [-WhatIf] [-Confirm] [<CommonParameters>]
```
```powershell
Invoke-FalconMalQuery [-YaraRule] <String> [[-FilterFiletype] <String[]>] [[-FilterMeta] <String[]>] [[-MinSize] <String>] [[-MaxSize] <String>] [[-MinDate] <String>] [[-MaxDate] <String>] [[-Limit] <Int32>] [-WhatIf] [-Confirm] [<CommonParameters>]
```
```powershell
Invoke-FalconMalQuery [-Type] <String> [-Value] <String> [[-FilterMeta] <String[]>] [[-Limit] <Int32>] -Fuzzy [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
POST /malquery/combined/fuzzy-search/v1
POST /malquery/queries/exact-search/v1
POST /malquery/queries/hunt/v1
```
### falconpy
[PostMalQueryExactSearchV1](https://github.com/CrowdStrike/falconpy/wiki/malquery#PostMalQueryExactSearchV1)<BR>[PostMalQueryHuntV1](https://github.com/CrowdStrike/falconpy/wiki/malquery#PostMalQueryHuntV1)<BR>[PostMalQueryFuzzySearchV1](https://github.com/CrowdStrike/falconpy/wiki/malquery#PostMalQueryFuzzySearchV1)
## USAGE
### Schedule a YARA search with hunt
```powershell
Invoke-FalconMalQuery -FilterFiletypes pe32 -MaxSize 1200KB -FilterMeta sha256, label, family -YaraRule "rule CrowdStrike_16142_01 : wiper { strings: $ = { 41 61 43 63 64 44 65 46 66 47 68 69 4B 4C 6C 4D 6D 6E 4E 6F 4F 70 50 72 52 73 53 54 74 55 75 56 76 77 57 78 79 5A 7A 33 32 2E 5C 45 62 67 6A 48 49 20 5F 59 51 42 3A 22 2F 40 } condition: all of them and filesize < 800KB }"
```
### Search for malware with an exact search
```powershell
Invoke-FalconMalQuery -FilterMeta sha256, type, size -FilterFiletype pe32, pe64 -MaxSize 1200KB -MinDate 2017/01/01 -Limit 20 -Type hex -Value 8948208b480833ca33f989502489482889782c8bd7
```
### Search for malware with a fuzzy search
```powershell
Invoke-FalconMalQuery -Limit 3 -Type ascii -Value ".8@bVn7r&k" -Fuzzy
```

_2023-04-25: PSFalcon v2.2.5_
