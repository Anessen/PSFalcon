# ConvertTo-FalconIoaExclusion
## SYNOPSIS
Output required fields to create an Indicator of Attack exclusion from a Falcon detection
## DESCRIPTION
Uses the 'behaviors' and 'device' properties of a detection to generate the necessary fields to create a new
Indicator of Attack exclusion. Specfically, it maps the following properties these fields:

behaviors.behavior_id > pattern_id
behaviors.display_name > pattern_name
behaviors.cmdline > cl_regex
behaviors.filepath > ifn_regex
device.groups > groups

The 'cl_regex' and 'ifn_regex' fields are escaped using the [regex]::Escape() PowerShell accelerator. The
'ifn_regex' output also replaces the NT device path ('Device/HarddiskVolume') with a wildcard.

If the detection involves a device that is not in any groups, it uses 'all' to target all host groups.

The resulting output can be passed to 'New-FalconIoaExclusion' to create an exclusion.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Detection|Object|Falcon detection content, including 'behaviors' and 'device'||||X||
## SYNTAX
```powershell
ConvertTo-FalconIoaExclusion [-Detection] <Object> [<CommonParameters>]
```
## USAGE

_2023-11-27: PSFalcon v2.2.6_
