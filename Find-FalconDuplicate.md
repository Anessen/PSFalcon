# Find-FalconDuplicate
## SYNOPSIS
Find potential duplicate hosts within your Falcon environment
## DESCRIPTION
If the 'Hosts' parameter is not provided, all Host information will be retrieved. An error will be
displayed if required fields 'cid', 'device_id', 'first_seen', 'last_seen', 'hostname' and any defined
'filter' value are not present.

Hosts are grouped by 'cid', 'hostname' and any defined 'filter' values, then sorted by 'last_seen' time. Any
result other than the one with the most recent 'last_seen' time is considered a duplicate host and is returned
within the output.

Hosts can be hidden from the Falcon console by piping the results of 'Find-FalconDuplicate' to
'Invoke-FalconHostAction' using the action 'hide_host'.

Requires 'Hosts: Read'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Hosts|Object[]|Array of detailed Host results||||||
|Filter|String[]|Property to determine duplicates, in addition to 'Hostname'|||`external_ip`<BR>`local_ip`<BR>`mac_address`<BR>`os_version`<BR>`platform_name`<BR>`serial_number`|||
|Platform|String|Filter hosts by platform|||`Linux`<BR>`Mac`<BR>`Windows`|||
## SYNTAX
```powershell
Find-FalconDuplicate [[-Hosts] <Object[]>] [[-Filter] <String[]>] [[-Platform] <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```
## USAGE
### Finding potential duplicate hosts
PSFalcon includes a command called `Find-FalconDuplicate` which will analyze the result of a detailed [Get-FalconHost](Get-FalconHost) output to find potential duplicates \(through grouping by hostname, then sorting by `last_seen` time and selecting all but the most recent\). Additional criteria can be added using the `Filter` parameter.
```powershell
Find-FalconDuplicate
```
### Create a CSV of potential duplicate hosts
```powershell
Find-FalconDuplicate | Export-Csv .\duplicates.csv
```
_See [Find duplicate hosts and hide them](https://github.com/CrowdStrike/psfalcon/blob/master/samples/hosts/find-duplicate-hosts-and-hide-them.ps1)._

_2023-04-25: PSFalcon v2.2.5_
