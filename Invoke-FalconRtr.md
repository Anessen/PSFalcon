﻿# Invoke-FalconRtr
## SYNOPSIS
Start a Real-time Response session, execute a command and output the result
## DESCRIPTION
Requires 'Real time response: Read', 'Real time response: Write' or 'Real time response (admin): Write' depending
on 'Command' provided, plus 'Hosts: Read' if using 'Include' or 'GroupId'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Command|String|Real-time Response command||||||
|Argument|String|Arguments to include with the command||||||
|Timeout|Int32|Length of time to wait for a result, in seconds [default: 600]|`30`|`600`||||
|QueueOffline|Boolean|Add non-responsive hosts to the offline queue||||||
|Include|String[]|Include additional properties|||`agent_version`<BR>`cid`<BR>`external_ip`<BR>`first_seen`<BR>`hostname`<BR>`last_seen`<BR>`local_ip`<BR>`mac_address`<BR>`os_build`<BR>`os_version`<BR>`platform_name`<BR>`product_type`<BR>`product_type_desc`<BR>`serial_number`<BR>`system_manufacturer`<BR>`system_product_name`<BR>`tags`|||
|GroupId|String|Host group identifier||||||
|HostId|String[]|Host identifier||||X|X|
## SYNTAX
```powershell
Invoke-FalconRtr [-Command] <String> [[-Argument] <String>] [[-Timeout] <Int32>] [[-QueueOffline] <Boolean>] [[-Include] <String[]>] -HostId <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```
```powershell
Invoke-FalconRtr [-Command] <String> [[-Argument] <String>] [[-Timeout] <Int32>] [[-QueueOffline] <Boolean>] [[-Include] <String[]>] -GroupId <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## USAGE
PSFalcon has a custom command named `Invoke-FalconRtr` that is designed to perform all the necessary steps to initiate a session with one or more hosts, send a command and output the results. `Invoke-FalconRtr` can target one or more host(s) \(`HostId`\), or the members of a Host Group \(`GroupId`\).

```powershell
Invoke-FalconRtr -Command ls -Arguments C:\Windows -HostId <id>, <id>
```
```powershell
Invoke-FalconRtr -Command ls -Arguments C:\Windows -GroupId <id>
```

**WARNING**: This command is not designed for a multi-step Real-time Response workflow and will negatively impact certain operations.

For instance, if you were to `cd` into a directory and attempt to `put` a file by running `Invoke-FalconRtr` twice, `Invoke-FalconRtr` will reset back to the root of your system drive between the `cd` and `put` commands, causing the file to be placed in the wrong directory.

If you find that your script needs to be more complex, you can follow the instructions below to create a custom Real-time Response workflow with multiple commands. PSFalcon includes commands for each Real-time Response permission level.

* `Invoke-FalconCommand`, `Confirm-FalconCommand`
* `Invoke-FalconResponderCommand`, `Confirm-FalconResponderCommand`
* `Invoke-FalconAdminCommand`, `Confirm-FalconAdminCommand`

### Use the offline queue
```powershell
Invoke-FalconRtr -Command runscript -Argument '-CloudFile="HelloWorld"' -HostId <id>, <id> -QueueOffline $true
```
### Submit identifiers using the pipeline
```powershell
Get-FalconHost -Filter "platform_name:'Windows'+last_seen:>'now-15m'" -All | Invoke-FalconRtr -Command runscript -Argument '-CloudFile="HelloWorld"'
```
### Run a falconscript
```powershell
$Json = [PSCustomObject]@{ Path = 'C:\windows\system32\notepad.exe' } | ConvertTo-Json -Compress
Invoke-FalconRtr -Command falconscript -Argument ('-Name="FileInfo" -JsonInput=```' + "'$Json'" + '```') -HostId <id>
```

_See [Upload and execute a local script](https://github.com/CrowdStrike/psfalcon/blob/master/samples/real-time_response/upload-and-execute-a-local-script.ps1)_.

_See [Upload and execute a local script as a secondary process](https://github.com/CrowdStrike/psfalcon/blob/master/samples/real-time_response/upload-and-execute-a-local-script-as-a-secondary-process.ps1)_.

_2024-02-08: PSFalcon v2.2.6_
