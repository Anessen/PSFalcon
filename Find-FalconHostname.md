# Find-FalconHostname
## SYNOPSIS
Find hosts using a list of hostnames
## DESCRIPTION
Perform hostname searches in groups of 100.

Requires 'Hosts: Read'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Path|String|Path to a plain text file containing hostnames||||||
|Include|String[]|Include additional properties|||`agent_version`<BR>`cid`<BR>`external_ip`<BR>`first_seen`<BR>`hostname`<BR>`last_seen`<BR>`local_ip`<BR>`mac_address`<BR>`os_build`<BR>`os_version`<BR>`platform_name`<BR>`product_type`<BR>`product_type_desc`<BR>`serial_number`<BR>`system_manufacturer`<BR>`system_product_name`<BR>`tags`|||
|Partial|Switch|Perform a non-exact search||||||
|Array|String[]|An array containing hostnames||||X||
## SYNTAX
```powershell
Find-FalconHostname [-Path] <String> [[-Include] <String[]>] [-Partial] [-WhatIf] [-Confirm] [<CommonParameters>]
```
```powershell
Find-FalconHostname [[-Include] <String[]>] [-Partial] -Array <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## USAGE
### Finding hosts with a list of hostnames
A search with [Get-FalconHost](Get-FalconHost) and a `hostname` filter is used to find `device_id` values that match a specific
hostname. To find hosts using a list of hostnames, you can [loop through the list](Code-Examples#retrieve-identifiers-using-a-list) or use `Find-FalconHostname`.

`Find-FalconHostname` can accept a list of hostnames as an array, or from a plaintext file containing a hostname
on each line. If a match is found, the `hostname` and `device_id` will be output, otherwise a warning message
will be generated.
```powershell
'hostname1','hostname2' | Find-FalconHostname
```
```powershell
Find-FalconHostname -Array 'hostname3','hostname4'
```
```powershell
Find-FalconHostname -Path .\my_hostname_list.txt
```

_2023-04-25: PSFalcon v2.2.5_
