# New-FalconSubmission
## SYNOPSIS
Submit a sample to the Falcon Intelligence Sandbox
## DESCRIPTION
'Sha256' values are retrieved from files that are uploaded using 'Send-FalconSample'. Files must be uploaded
before they can be provided to the Falcon Intelligence Sandbox.

Requires 'Sandbox (Falcon Intelligence): Write'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|EnvironmentId|String|Analysis environment|||`android`<BR>`macOS_10.15`<BR>`ubuntu16_x64`<BR>`win7_x64`<BR>`win7_x86`<BR>`win10_x64`|||
|Url|String|A webpage or file URL||||||
|ActionScript|String|Runtime script for sandbox analysis|||`default`<BR>`default_maxantievasion`<BR>`default_randomfiles`<BR>`default_randomtheme`<BR>`default_openie`|||
|CommandLine|String|Command line script passed to the submitted file at runtime||||||
|SystemDate|String|A custom date to use in the analysis environment||||||
|SystemTime|String|A custom time to use in the analysis environment||||||
|DocumentPassword|String|Auto-filled for Adobe or Office files that prompt for a password||||||
|NetworkSetting|String|Network settings to use in the analysis environment|||`default`<BR>`tor`<BR>`simulated`<BR>`offline`|||
|EnableTor|Boolean|Route traffic via TOR||||||
|UserTag|String[]|Tags to categorize the submission||||||
|SubmitName|String|Submission name|||||X|
|Sha256|String|Sha256 hash value||||X|X|
## SYNTAX
```powershell
New-FalconSubmission [-EnvironmentId] <String> [[-Url] <String>] [[-ActionScript] <String>] [[-CommandLine] <String>] [[-SystemDate] <String>] [[-SystemTime] <String>] [[-DocumentPassword] <String>] [[-NetworkSetting] <String>] [[-EnableTor] <Boolean>] [[-UserTag] <String[]>] [[-SubmitName] <String>] [[-Sha256] <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
POST /falconx/entities/submissions/v1
```
### falconpy
[Submit](https://github.com/CrowdStrike/falconpy/wiki/falconx-sandbox#Submit)
## USAGE
### Submit an uploaded sample for analysis in a sandbox environment
The file submitted to the Falcon Intelligence Sandbox must be previously uploaded through `Send-FalconSample`.
```powershell
New-FalconSubmission -Sha256 <sha256> -EnvironmentId win7_x86 -SubmitName virus.exe
```
_See [Send-FalconSample](Send-FalconSample)._

_2023-04-25: PSFalcon v2.2.5_
