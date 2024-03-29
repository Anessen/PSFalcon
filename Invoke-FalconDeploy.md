# Invoke-FalconDeploy
## SYNOPSIS
Deploy and run an executable using Real-time Response
## DESCRIPTION
'Put' files will be checked for identical file names, and if any are found, the Sha256 hash values will be
compared between your local and cloud files. If they are different, a prompt will appear asking which file to use.

After ensuring that the 'Put' file is available, a Real-time Response session will be started for the designated
host(s) (or members of the Host Group), 'mkdir' will create a folder ('FalconDeploy_<FileDateTime>') within the
appropriate temporary folder (\Windows\Temp or /tmp), 'cd' will navigate to the new folder, and the target file or
archive will be 'put' into that folder. If the target is an archive, it will be extracted, and the designated
'Run' file will be executed. If the target is a file, it will be 'run'.

Details of each step will be output to a CSV file in your current directory.

Requires 'Hosts: Read', 'Real time response (admin): Write'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|File|String|Name of a 'CloudFile' or path to a local executable to upload||||||
|Archive|String|Name of a 'CloudFile' or path to a local archive (zip, tar, tar.gz, tgz) to upload||||||
|Run|String|Name of the file to run once extracted from the target archive||||||
|Argument|String|Arguments to include when running the target executable||||||
|Timeout|Int32|Length of time to wait for a result, in seconds [default: 60]|`30`|`600`||||
|QueueOffline|Boolean|Add non-responsive Hosts to the offline queue||||||
|Include|String[]|Include additional properties|||`agent_version`<BR>`cid`<BR>`external_ip`<BR>`first_seen`<BR>`hostname`<BR>`last_seen`<BR>`local_ip`<BR>`mac_address`<BR>`os_build`<BR>`os_version`<BR>`platform_name`<BR>`product_type`<BR>`product_type_desc`<BR>`serial_number`<BR>`system_manufacturer`<BR>`system_product_name`<BR>`tags`|||
|GroupId|String|Host group identifier||||||
|HostId|String[]|Host identifier||||X|X|
## SYNTAX
```powershell
Invoke-FalconDeploy [-File] <String> [[-Argument] <String>] [[-Timeout] <Int32>] [[-QueueOffline] <Boolean>] [[-Include] <String[]>] -HostId <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```
```powershell
Invoke-FalconDeploy [-File] <String> [[-Argument] <String>] [[-Timeout] <Int32>] [[-QueueOffline] <Boolean>] [[-Include] <String[]>] -GroupId <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```
```powershell
Invoke-FalconDeploy -Archive <String> [-Run] <String> [[-Argument] <String>] [[-Timeout] <Int32>] [[-QueueOffline] <Boolean>] [[-Include] <String[]>] -GroupId <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```
```powershell
Invoke-FalconDeploy -Archive <String> [-Run] <String> [[-Argument] <String>] [[-Timeout] <Int32>] [[-QueueOffline] <Boolean>] [[-Include] <String[]>] -HostId <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## USAGE
`Invoke-FalconDeploy` was developed to support mass-deployment of Falcon Forensics, but has since been expanded to support additional file types. It is designed to upload a file to your 'Put Files' library, create a session with target hosts, push the file to those hosts, then execute it (after expanding archives, when appropriate) and output the results to CSV.

The `File` and `Run` parameters accept exectuables or scripts (`.ps1`, `.sh`, `.zsh`) while `Archive` accepts `.zip`, `.tar`, `tar.gz` or `.tgz`.

Files to be delivered to the host will be stored in the appropriate temporary directory (`C:\Windows\Temp` or `/tmp`) under a unique folder each time the command is run (`FalconDeploy_<FileDateTime>`).

**NOTE**: Because Real-time Response does not interact with logged in users, the executable must be able to be run silently and without user interaction.
### Upload and execute File.exe
```powershell
Invoke-FalconDeploy -File .\File.exe -HostId <id>, <id> [-QueueOffline]
```
### Perform a silent Notepad++ installation on members of a host group
```powershell
Invoke-FalconDeploy -File ./npp.8.2.1.Installer.x64.exe -Argument '/S' -GroupId <group_id>
```
### Upload an archive and execute a file inside
```powershell
Archive:  ./npp_installer.zip
  Length      Date    Time    Name
---------  ---------- -----   ----
  4399816  04-20-2022 09:51   npp.8.2.1.Installer.x64.exe
      173  03-28-2022 12:35   some_other_file.csv
---------                     -------
  4399989                     2 files

Invoke-FalconDeploy -Archive npp_installer.zip -Run 'npp.8.2.1.Installer.x64.exe' -Argument '/S' -HostId <id>
```
Results will be output to `FalconDeploy_<FileDateTime>.csv` within your local directory.

_2023-04-25: PSFalcon v2.2.5_
