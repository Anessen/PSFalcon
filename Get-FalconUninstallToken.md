# Get-FalconUninstallToken
## SYNOPSIS
Retrieve an uninstallation or maintenance token
## DESCRIPTION
Requires 'Sensor update policies: Write', plus related permission(s) for 'Include' selection(s).
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|AuditMessage|String|Audit log comment||||||
|Include|String[]|Include additional properties|||`agent_version`<BR>`cid`<BR>`external_ip`<BR>`first_seen`<BR>`hostname`<BR>`last_seen`<BR>`local_ip`<BR>`mac_address`<BR>`os_build`<BR>`os_version`<BR>`platform_name`<BR>`product_type`<BR>`product_type_desc`<BR>`serial_number`<BR>`system_manufacturer`<BR>`system_product_name`<BR>`tags`|||
|Id|String|Host identifier||||X|X|
## SYNTAX
```powershell
Get-FalconUninstallToken [[-AuditMessage] <String>] [[-Include] <String[]>] [-Id] <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
POST /policy/combined/reveal-uninstall-token/v1
```
### falconpy
[revealUninstallToken](https://github.com/CrowdStrike/falconpy/wiki/sensor-update-policy#revealUninstallToken)
## USAGE
### Finding a token for a host
```powershell
Get-FalconUninstallToken -Id <id>
```
### Finding the maintenance token that applies to any host within a given policy
```powershell
Get-FalconUninstallToken -Id MAINTENANCE
```
### Create a CSV of all available uninstall tokens
```powershell
Get-FalconHost -All | Get-FalconUninstallToken -Include hostname | Export-Csv .\token_list.csv -NoTypeInformation
```
### Create a CSV of uninstall tokens using a list of device_ids in a text file
```powershell
Get-Content .\device_id.txt | Get-FalconUninstallToken | Export-Csv .\token_list.csv -NoTypeInformation
```

_2023-04-25: PSFalcon v2.2.5_
