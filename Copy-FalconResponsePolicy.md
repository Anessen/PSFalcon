# Copy-FalconResponsePolicy
## SYNOPSIS
Duplicate a Real-time Response policy
## DESCRIPTION
The specified Real-time Response policy will be duplicated without assigned Host Groups. If a policy description
is not supplied, the description from the existing policy will be used.

Requires 'Response policies: Read', 'Response policies: Write'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Name|String|Name for the policy that will be created||||||
|Description|String|Description for the policy that will be created||||||
|Id|String|Identifier of policy to be copied||||X|X|
## SYNTAX
```powershell
Copy-FalconResponsePolicy [-Name] <String> [[-Description] <String>] [-Id] <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## USAGE

_2023-04-25: PSFalcon v2.2.5_
