# New-FalconReconRule
## SYNOPSIS
Create Falcon Intelligence Recon monitoring rules
## DESCRIPTION
Requires 'Monitoring rules (Falcon Intelligence Recon): Write'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Array|Object[]|An array of monitoring rules to create in a single request||||X||
|Name|String|Monitoring rule name||||||
|Topic|String|Monitoring rule topic|||`SA_ALIAS`<BR>`SA_AUTHOR`<BR>`SA_BIN`<BR>`SA_BRAND_PRODUCT`<BR>`SA_CUSTOM`<BR>`SA_CVE`<BR>`SA_DOMAIN`<BR>`SA_EMAIL`<BR>`SA_IP`<BR>`SA_THIRD_PARTY`<BR>`SA_VIP`|||
|Filter|String|[Falcon Query Language](Filtering-Results) expression to limit results||||||
|Priority|String|Monitoring rule priority|||`high`<BR>`medium`<BR>`low`|||
|Permission|String|Permission level [public: 'All Intel users', private: 'Recon Admins']|||`private`<BR>`public`|||
|BreachMonitoring|Boolean|Monitor for breach data||||||
|SubstringMatching|Boolean|Monitor for substring matches||||||
## SYNTAX
```powershell
New-FalconReconRule [-Name] <String> [-Topic] <String> [-Filter] <String> [-Priority] <String> [-Permission] <String> [[-BreachMonitoring] <Boolean>] [[-SubstringMatching] <Boolean>] [-WhatIf] [-Confirm] [<CommonParameters>]
```
```powershell
New-FalconReconRule -Array <Object[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
POST /recon/entities/rules/v1
```
### falconpy
[CreateRulesV1](https://github.com/CrowdStrike/falconpy/wiki/recon#CreateRulesV1)
## USAGE
### Creating a monitoring rule
```powershell
New-FalconReconRule -Name psfalcon_example -Topic SA_AUTHOR -Filter "author:'example_author'" -Priority low -Permission private
```
### Creating multiple monitoring rules in a single request
```powershell
$Array = @(
    @{
        name = "psfalcon_example_1"
        topic = "SA_BRAND_PRODUCT"
        filter = "phrase:'psfalcon_example_phrase'"
        priority = "low"
        permissions = "private"
    },
    @{
        name = "psfalcon_example_2"
        topic = "SA_BIN"
        filter = "ccbin:'1234'"
        priority = "medium"
        permissions = "public"
    }
)
New-FalconReconRule -Array $Array
```

_2023-04-25: PSFalcon v2.2.5_
