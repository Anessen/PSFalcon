# Send-FalconEvent
## SYNOPSIS
Create Falcon LogScale events from PSFalcon command results
## DESCRIPTION
Uses the pre-defined 'Path' and 'Token' values from 'Register-FalconEventCollector' to create events from the
output provided by a PSFalcon command.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Object|Object|PSFalcon command output||||X||
## SYNTAX
```powershell
Send-FalconEvent [-Object] <Object> [<CommonParameters>]
```
## USAGE
## Send objects to Falcon LogScale
Once a collector has been defined through [Register-FalconEventCollector](Register-FalconEventCollector), any `[PSCustomObject]` can be sent to
Falcon LogScale.
```powershell
Get-FalconHost -Limit 1 -Detailed | Send-FalconEvent
```
```powershell
Send-FalconEvent -Object ([PSCustomObject]@{ Example = 'my_string' })
```

_2023-04-25: PSFalcon v2.2.5_
