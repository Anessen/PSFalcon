# New-FalconQuickScan
## SYNOPSIS
Submit a volume of files to Falcon QuickScan
## DESCRIPTION
'Id' values (Sha256 hashes) are retrieved from files that are uploaded using 'Send-FalconSample'. Files must be
uploaded before they can be used with Falcon QuickScan.

Time required for analysis increases with the number of samples in a volume but usually takes less than 1 minute.

Requires 'Quick Scan (Falcon Intelligence): Write'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Id|String[]|Sha256 hash value||||X|X|
## SYNTAX
```powershell
New-FalconQuickScan [-Id] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
POST /scanner/entities/scans/v1
```
### falconpy
[ScanSamples](https://github.com/CrowdStrike/falconpy/wiki/quick-scan#ScanSamples)
## USAGE
### Submit files to QuickScan
The files submitted to Falcon Intelligence QuickScan must be previously uploaded through `Send-FalconSample`.
```powershell
New-FalconQuickScan -Id <sha256>, <sha256>
```
_See [Send-FalconSample](Send-FalconSample)._

_2023-04-25: PSFalcon v2.2.5_
