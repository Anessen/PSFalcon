# Get-FalconDiscoverAwsAccount
## SYNOPSIS
Search for Falcon Discover for Cloud AWS accounts
## DESCRIPTION
Requires 'AWS accounts: Read'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Id|String[]|AWS account identifier||||X|X|
|OrganizationId|String[]|AWS organization identifier||||||
|ScanType|String|Scan type|||`full`<BR>`dry`|||
|Status|String|AWS account status|||`provisioned`<BR>`operational`|||
|Migrated|Boolean|Account migration status||||||
|Limit|Int32|Maximum number of results per request|`1`|`500`||||
|Offset|Int32|Position to begin retrieving results||||||
|All|Switch|Repeat requests until all available results are retrieved||||||
|Total|Switch|Display total result count instead of results||||||
## SYNTAX
```powershell
Get-FalconDiscoverAwsAccount [-Id <String[]>] [[-OrganizationId] <String[]>] [[-ScanType] <String>] [[-Status] <String>] [[-Migrated] <Boolean>] [[-Limit] <Int32>] [-Offset <Int32>] [-All] [-Total] [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
GET /cloud-connect-aws/entities/account/v2
```
### falconpy
[GetD4CAwsAccount](https://github.com/CrowdStrike/falconpy/wiki/cloud-connect-aws#GetD4CAwsAccount)
## USAGE
### Retrieve details by AWS account ID
```powershell
Get-FalconDiscoverAwsAccount -Id <id>, <id>
```
### Retrieve AWS account details by query
```powershell
Get-FalconDiscoverAwsAccount -Filter "provisioning_state:'initiated'" -Detailed
```

_2023-04-25: PSFalcon v2.2.5_
