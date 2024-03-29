# New-FalconResponsePolicy
## SYNOPSIS
Create Real-time Response policies
## DESCRIPTION
Requires 'Response policies: Write'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Array|Object[]|An array of policies to create in a single request||||X||
|Name|String|Policy name||||||
|PlatformName|String|Operating system platform|||`Windows`<BR>`Mac`<BR>`Linux`|||
|Description|String|Policy description||||||
|Setting|Object[]|||||||
## SYNTAX
```powershell
New-FalconResponsePolicy [-Name] <String> [-PlatformName] <String> [[-Description] <String>] [[-Setting] <Object[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```
```powershell
New-FalconResponsePolicy -Array <Object[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
POST /policy/entities/response/v1
```
### falconpy
[createRTResponsePolicies](https://github.com/CrowdStrike/falconpy/wiki/response-policies#createRTResponsePolicies)
## USAGE
### Create a policy
```powershell
New-FalconResponsePolicy -PlatformName Windows -Name 'Test RTR Policy 2' -Description 'Short description of test RTR policy 2.'
```

_2023-04-25: PSFalcon v2.2.5_
