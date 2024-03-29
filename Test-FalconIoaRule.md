# Test-FalconIoaRule
## SYNOPSIS
Validate fields and patterns of a custom Indicator of Attack rule
## DESCRIPTION
Requires 'Custom IOA rules: Write'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Field|Object[]|An array of rule properties|||||X|
## SYNTAX
```powershell
Test-FalconIoaRule [-Field] <Object[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
POST /ioarules/entities/rules/validate/v1
```
### falconpy
[validate](https://github.com/CrowdStrike/falconpy/wiki/custom-ioa#validate)
## USAGE
### Validating field values
```powershell
$Field = @(
    @{
        label = 'Grandparent Image Filename'
        name = 'GrandparentImageFilename'
        type = 'excludable'
        values = @(
            @{
                label = 'include'
                value = '.+attacker.exe'
            }
        )
    }
)
Test-FalconIoaRule -Field $Field
```

_2023-04-25: PSFalcon v2.2.5_
