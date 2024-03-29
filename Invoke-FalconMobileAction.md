# Invoke-FalconMobileAction
## SYNOPSIS
Trigger on-boarding process for a mobile device
## DESCRIPTION
Requires 'Mobile Enrollment: Write'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Name|String|Action to perform|||`enroll`<BR>`re-enroll`|||
|ExpiresAt|String|Expiration time [default: 30 days]||||||
|Email|String[]|Email address||||X|X|
## SYNTAX
```powershell
Invoke-FalconMobileAction [-Name] <String> [[-ExpiresAt] <String>] [-Email] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
POST /enrollments/entities/details/v3
```
### falconpy
[RequestDeviceEnrollmentV3](https://github.com/CrowdStrike/falconpy/wiki/mobile-enrollment#RequestDeviceEnrollmentV3)
## USAGE

_2023-04-25: PSFalcon v2.2.5_
