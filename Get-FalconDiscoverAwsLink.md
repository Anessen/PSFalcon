# Get-FalconDiscoverAwsLink
## SYNOPSIS
Retrieve previously generated Falcon Discover AWS CloudFormation links
## DESCRIPTION
Requires 'AWS accounts: Read'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Region|String|AWS region||||||
## SYNTAX
```powershell
Get-FalconDiscoverAwsLink [[-Region] <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
GET /cloud-connect-aws/entities/console-setup-urls/v1
```
### falconpy
[GetD4CAwsConsoleSetupURLs](https://github.com/CrowdStrike/falconpy/wiki/cloud-connect-aws#GetD4CAwsConsoleSetupURLs)
## USAGE

_2023-04-25: PSFalcon v2.2.5_
