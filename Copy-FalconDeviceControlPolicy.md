# Copy-FalconDeviceControlPolicy
## SYNOPSIS
Duplicate a Falcon Device Control policy
## DESCRIPTION
The specified Falcon Device Control policy will be duplicated without assigned Host Groups. If a policy
description is not supplied, the description from the existing policy will be used.

Requires 'Device control policies: Read', 'Device control policies: Write'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Name|String|Name for the policy that will be created||||||
|Description|String|Description for the policy that will be created||||||
|Id|String|Identifier of policy to be copied||||X|X|
## SYNTAX
```powershell
Copy-FalconDeviceControlPolicy [-Name] <String> [[-Description] <String>] [-Id] <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## USAGE

_2023-04-25: PSFalcon v2.2.5_
