# New-FalconDeviceControlPolicy
## SYNOPSIS
Create Falcon Device Control policies
## DESCRIPTION
Requires 'Device control policies: Write'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Array|Object[]|An array of policies to create in a single request||||X||
|Name|String|Policy name||||||
|PlatformName|String|Operating system platform|||`Windows`<BR>`Mac`<BR>`Linux`|||
|Description|String|Policy description||||||
|Setting|Object|||||||
## SYNTAX
```powershell
New-FalconDeviceControlPolicy [-Name] <String> [-PlatformName] <String> [[-Description] <String>] [[-Setting] <Object>] [-WhatIf] [-Confirm] [<CommonParameters>]
```
```powershell
New-FalconDeviceControlPolicy -Array <Object[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
POST /policy/entities/device-control/v1
```
### falconpy
[createDeviceControlPolicies](https://github.com/CrowdStrike/falconpy/wiki/device-control-policies#createDeviceControlPolicies)
## USAGE
### Create a policy
```powershell
New-FalconDeviceControlPolicy -PlatformName Windows -Name 'My Device Control Policy' -Description 'Short description of my Device Control policy.'
```

_2023-04-25: PSFalcon v2.2.5_
