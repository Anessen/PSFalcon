# Edit-FalconReconRule
## SYNOPSIS
Modify a Falcon Intelligence Recon monitoring rule
## DESCRIPTION
Requires 'Monitoring rules (Falcon Intelligence Recon): Write'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Array|Object[]|An array of monitoring rules to modify in a single request||||X||
|Id|String|Monitoring rule identifier||||||
|Name|String|Monitoring rule name||||||
|Filter|String|Monitoring rule filter||||||
|Priority|String|Monitoring rule priority|||`high`<BR>`medium`<BR>`low`|||
|Permission|String|Permission level [public: 'All Intel users', private: 'Recon Admins']|||`private`<BR>`public`|||
|BreachMonitoring|Boolean|Monitor for breach data||||||
|SubstringMatching|Boolean|Monitor for substring matches||||||
## SYNTAX
```powershell
Edit-FalconReconRule [-Id] <String> [-Name] <String> [-Filter] <String> [-Priority] <String> [-Permission] <String> [[-BreachMonitoring] <Boolean>] [[-SubstringMatching] <Boolean>] [-WhatIf] [-Confirm] [<CommonParameters>]
```
```powershell
Edit-FalconReconRule -Array <Object[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
PATCH /recon/entities/rules/v1
```
### falconpy
[UpdateRulesV1](https://github.com/CrowdStrike/falconpy/wiki/recon#UpdateRulesV1)
## USAGE
### Updating a monitoring rule
```powershell
Edit-FalconReconRule -Id <id> -Name psfalcon_example_updated -Priority medium
```
### Updating multiple monitoring rules in a single request
```powershell
$Array = @(
    @{
        id = <id>
        priority = "high"
    },
    @{
        id = <id>
        priority = "high"
    }
)
Edit-FalconReconRule -Array $Array
```

_2023-04-25: PSFalcon v2.2.5_
