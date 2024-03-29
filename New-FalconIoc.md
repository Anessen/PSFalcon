# New-FalconIoc
## SYNOPSIS
Create custom indicators
## DESCRIPTION
Requires 'IOC Manager APIs: Write'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Array|Object[]|An array of indicators to create in a single request||||X||
|Action|String|Action to perform when a host observes the indicator||||||
|Platform|String[]|Operating system platform||||||
|Source|String|Origination source|`1`|`256`||||
|Severity|String|Severity level||||||
|Description|String|Indicator description||||||
|Filename|String|Indicator filename,used with hash values||||||
|Tag|String[]|Indicator tag||||||
|MobileAction|String|Action to perform when a mobile device observes the indicator|||`no_action`<BR>`allow`<BR>`detect`<BR>`prevent`|||
|HostGroup|String[]|Host group identifier||||||
|AppliedGlobally|Boolean|Assign to all host groups||||||
|Expiration|String|Expiration date. When an indicator expires,its action is set to 'no_action' but it remains in your indicator list.||||||
|Comment|String|Audit log comment||||||
|Retrodetect|Boolean|Generate retroactive detections for hosts that have observed the indicator||||||
|IgnoreWarning|Boolean|Ignore warnings and create all indicators||||||
|Type|String|Indicator type||||||
|Value|String|String representation of the indicator||||||
## SYNTAX
```powershell
New-FalconIoc [-Action] <String> [-Platform] <String[]> [[-Source] <String>] [[-Severity] <String>] [[-Description] <String>] [[-Filename] <String>] [[-Tag] <String[]>] [[-MobileAction] <String>] [[-HostGroup] <String[]>] [[-AppliedGlobally] <Boolean>] [[-Expiration] <String>] [[-Comment] <String>] [[-Retrodetect] <Boolean>] [[-IgnoreWarning] <Boolean>] [-Type] <String> [-Value] <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```
```powershell
New-FalconIoc -Array <Object[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```
```powershell
New-FalconIoc [[-Comment] <String>] [[-Retrodetect] <Boolean>] [[-IgnoreWarning] <Boolean>] [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
POST /iocs/entities/indicators/v1
```
### falconpy
[indicator_create_v1](https://github.com/CrowdStrike/falconpy/wiki/ioc#indicator_create_v1)
## USAGE
### Creating a domain indicator
```powershell
New-FalconIoc -Type domain -Value example01.com -Action detect -Severity medium -Description 'test description' -Platforms windows, mac, linux -Tags test_tag -HostGroup <host_group_id>, <host_group_id> -Expiration 2021-05-01
```
### Creating multiple indicators in a single request
```powershell
$Array = @(
    @{
        type = 'domain'
        value = 'example01.com'
        action = 'detect'
        severity = 'medium'
        description = 'test description'
        platforms = @('windows', 'mac', 'linux')
        tags = @('test_tag')
        host_groups = @('<id>')
    },
    @{
        type = 'sha256'
        value = 'a88787d8ff144c502c7f5cffaafe2cc588d86079f9de88304c26b0cb99ce91cc'
        source = 'bd20201216'
        filename = 'iexplore.exe'
        action = 'prevent'
        severity = 'high'
        description = 'test block description'
        platforms = @('windows')
        tags = @('test_tag', 'test_tag2')
        applied_globally = $true
    }
)
New-FalconIoc -Array $Array
```

_2023-11-27: PSFalcon v2.2.6_
