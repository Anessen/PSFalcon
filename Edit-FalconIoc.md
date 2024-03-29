# Edit-FalconIoc
## SYNOPSIS
Modify custom indicators
## DESCRIPTION
Requires 'IOC Manager APIs: Write'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Array|Object[]|An array of indicators to modify in a single request||||X||
|Action|String|Action to perform when a host observes the indicator||||||
|Platform|String[]|Operating system platform||||||
|Source|String|Origination source|`1`|`256`||||
|Severity|String|Severity level||||||
|Description|String|Indicator description||||||
|Filename|String|Indicator filename, used with hash values||||||
|Tag|String[]|Indicator tag||||||
|MobileAction|String|Action to perform when a mobile device observes the indicator|||`no_action`<BR>`allow`<BR>`detect`<BR>`prevent`|||
|HostGroup|String[]|Host group identifier||||||
|AppliedGlobally|Boolean|Assign to all host groups||||||
|Expiration|String|Expiration date. When an indicator expires, its action is set to 'no_action' but it remains in your indicator list.||||||
|Comment|String|Audit log comment||||||
|FromParent|Boolean|Inheritance from parent CID||||||
|Retrodetect|Boolean|Generate retroactive detections for hosts that have observed the indicator||||||
|IgnoreWarning|Boolean|Ignore warnings and modify all indicators||||||
|Id|String|Indicator identifier||||||
## SYNTAX
```powershell
Edit-FalconIoc [[-Action] <String>] [[-Platform] <String[]>] [[-Source] <String>] [[-Severity] <String>] [[-Description] <String>] [[-Filename] <String>] [[-Tag] <String[]>] [[-MobileAction] <String>] [[-HostGroup] <String[]>] [[-AppliedGlobally] <Boolean>] [[-Expiration] <String>] [[-Comment] <String>] [[-FromParent] <Boolean>] [[-Retrodetect] <Boolean>] [[-IgnoreWarning] <Boolean>] [-Id] <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```
```powershell
Edit-FalconIoc -Array <Object[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
PATCH /iocs/entities/indicators/v1
```
### falconpy
[indicator_update_v1](https://github.com/CrowdStrike/falconpy/wiki/ioc#indicator_update_v1)
## USAGE
### Updating an indicator by identifier
```powershell
Edit-FalconIoc -Id <id> -Source testSource -Action detect -Severity low -Description 'test description update' -Platforms windows -Tags test_tag2 -HostGroup all -Expiration '2021-05-01T12:00:00Z'
```

_2023-11-27: PSFalcon v2.2.6_
