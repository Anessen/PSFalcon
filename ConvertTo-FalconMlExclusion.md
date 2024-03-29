# ConvertTo-FalconMlExclusion
## SYNOPSIS
Output required fields to create a Machine Learning exclusion from a Falcon detection
## DESCRIPTION
Uses the 'behaviors' and 'device' properties of a detection to generate the necessary fields to create a new
Machine Learning exclusion. Specfically, it maps the following properties these fields:

behaviors.filepath > value
device.groups > groups

The 'value' field is stripped of any leading NT file path ('Device/HarddiskVolume').

If the detection involves a device that is not in any groups,it uses 'all' to target all host groups.

The resulting output can be passed to 'New-FalconMlExclusion' to create an exclusion.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Detection|Object|Falcon detection content, including 'behaviors' and 'device'||||X||
## SYNTAX
```powershell
ConvertTo-FalconMlExclusion [-Detection] <Object> [<CommonParameters>]
```
## USAGE

_2023-11-27: PSFalcon v2.2.6_
