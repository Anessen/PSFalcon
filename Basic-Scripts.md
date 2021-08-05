***
The code provided below is for example purposes only and is offered 'as is' with no support. For specific pieces of code that can help construct scripts, _see [Code Examples](https://github.com/CrowdStrike/psfalcon/wiki/Code-Examples)_.
***
### Detections
* [Assign detections involving a specific file to a user](https://github.com/CrowdStrike/psfalcon/wiki/Basic-Scripts#assign-detections-involving-a-specific-file-to-a-user)
* [Find and hide large numbers of detections](https://github.com/CrowdStrike/psfalcon/wiki/Basic-Scripts#find-and-hide-large-numbers-of-detections)
### Hosts
* [Add a list of hostnames to a host group](https://github.com/CrowdStrike/psfalcon/wiki/Basic-Scripts#add-a-list-of-hostnames-to-a-host-group)
* [Hide hosts based on last_seen time](https://github.com/CrowdStrike/psfalcon/wiki/Basic-Scripts#hide-hosts-based-on-last_seen-time)
* [Find duplicate hosts and hide them](https://github.com/CrowdStrike/psfalcon/wiki/Basic-Scripts#find-duplicate-hosts-and-hide-them)
* [Network contain a device by Hostname](https://github.com/CrowdStrike/psfalcon/wiki/Basic-Scripts#network-contain-a-device-by-hostname)
* [Network contain a list of Hostnames from a CSV file](https://github.com/CrowdStrike/psfalcon/wiki/Basic-Scripts#network-contain-a-list-of-hostnames-from-a-csv-file)
* [Get host information from multiple Falcon instances](https://github.com/CrowdStrike/psfalcon/wiki/Basic-Scripts#get-host-information-from-multiple-falcon-instances)
### Host Groups
* [Verify that a list of Host Groups exist within Child CIDs](https://github.com/CrowdStrike/psfalcon/wiki/Basic-Scripts#verify-that-a-list-of-host-groups-exist-within-child-cids)
### Policies
* [Modify all Sensor Visibility Exclusions to include an additional Host Group](https://github.com/CrowdStrike/psfalcon/wiki/Basic-Scripts#modify-all-sensor-visibility-exclusions-to-include-an-additional-host-group)
* [Assign a list of Host Group names to a specific Policy Id within a list of Child CIDs](https://github.com/CrowdStrike/psfalcon/wiki/Basic-Scripts#modify-all-sensor-visibility-exclusions-to-include-an-additional-host-group)
* [Output a list of assigned Host Groups for designated Policy ids within child CIDs](https://github.com/CrowdStrike/psfalcon/wiki/Basic-Scripts#output-a-list-of-assigned-host-groups-for-designated-policy-ids-within-child-cids)
* [Add a list of combined_id exceptions to a Device Control policy](https://github.com/CrowdStrike/psfalcon/wiki/Basic-Scripts#add-a-list-of-combined_id-exceptions-to-a-device-control-policy)
### Real-time Response
* [Run a command against a group of devices](https://github.com/CrowdStrike/psfalcon/wiki/Basic-Scripts#run-a-command-against-a-group-of-devices)
* [Upload and execute a local script](https://github.com/CrowdStrike/psfalcon/wiki/Basic-Scripts#upload-and-execute-a-local-script)
* [Upload and execute a local script as a secondary process](https://github.com/CrowdStrike/psfalcon/wiki/Basic-Scripts#upload-and-execute-a-local-script)
### Sensor Installers
* [Download the installer package assigned to a Sensor Update policy](https://github.com/CrowdStrike/psfalcon/wiki/Basic-Scripts#download-the-installer-package-assigned-to-a-sensor-update-policy)
### Threat Intelligence
* [Export domain and IP indicators updated within the last week to CSV](https://github.com/CrowdStrike/psfalcon/wiki/Basic-Scripts#export-domain-and-ip-indicators-updated-within-the-last-week-to-csv)
### Vulnerabilities
* [Create a report with additional Host fields](https://github.com/CrowdStrike/psfalcon/wiki/Basic-Scripts#export-domain-and-ip-indicators-updated-within-the-last-week-to-csv)
***
# Detections
## Assign detections involving a specific file to a user
```powershell
#Requires -Version 5.1 -Modules @{ModuleName="PSFalcon";ModuleVersion='2.0'}
param(
    [Parameter(Mandatory = $true,
        Position = 1)]
    [string] $Username,

    [Parameter(Mandatory = $true,
        Position = 2)]
    [string] $Filename
)
# Get User identifier
$Uuid = Get-FalconUser -Usernames $Username -ErrorAction SilentlyContinue

if (-not $Uuid) {
    throw "Invalid username: '$Username'"
}
# Get Detection identifiers involving $Filename
$Ids = Get-FalconDetection -Filter "behaviors.filename:'$Filename'" -All

if (-not $Ids) {
    throw "No detections found matching '$Filename'"
}
# Notify user that detections are being assigned
Write-Host "Assigning $($Ids.count) detections involving '$Filename' to '$Username'..."

# Modify detections
Edit-FalconDetection -Ids $Ids -Status in_progress -AssignedToUuid $Uuid
```
## Find and hide large numbers of detections
```powershell
#Requires -Version 5.1 -Modules @{ModuleName="PSFalcon";ModuleVersion='2.0'}
param(
    [Parameter(Mandatory = $true)]
    [string] $Filename
)
do {
    # Gather up to 1,000 detections (maximum for an edit request) involving $Filename
    $Ids = Get-FalconDetection -Filter "behaviors.filename:'$Filename'" -Limit 1000

    if ($Ids) {
        # Export list of ids being hidden
        $Ids | Out-File -FilePath $pwd\hidden_detections.txt -Append -Force

        # Hide group of detections
        Edit-FalconDetection -Ids $Ids -ShowInUi $false

        # Pause to give the API time to clear them out before the next request
        Start-Sleep -Seconds 5
    }
} while (
    # Exit once no more detections are available
    $Ids
)
```
# Hosts
## Add a list of hostnames to a host group
**NOTE**: This script expects a text file that contains case-sensitive hostnames (one per line) for the `-Path` parameter.
```powershell
#Requires -Version 5.1 -Modules @{ModuleName="PSFalcon";ModuleVersion='2.0'}
param(
    [Parameter(Mandatory = $true,
        Position = 1)]
    [ValidatePattern('\.csv$')]
    [string] $Path,

    [Parameter(Mandatory = $true,
        Position = 2)]
    [ValidatePattern('^\w{32}$')]
    [string] $GroupId
)
$Hostnames = (Get-Content $Path).Normalize()
$Hosts = for ($i = 0; $i -lt $Hostnames.count; $i += 20) {
    # Retrieve the device_id for hostnames in groups of 20
    $Filter = ($Hostnames[$i..($i + 19)] | ForEach-Object {
        if ($_ -ne '') {
            "hostname:['$_']"
        }
    }) -join ','
    Get-FalconHost -Filter $Filter
}
# Add hosts to group
Invoke-FalconHostGroupAction -Name add-hosts -Id $GroupId -HostIds $Hosts
```
## Hide hosts based on last_seen time
```powershell
#Requires -Version 5.1 -Modules @{ModuleName="PSFalcon";ModuleVersion='2.0'}
param(
    [Parameter(Mandatory = $true)]
    [int] $Days
)
$Param = @{
    Filter = "last_seen:<'Last $Days days'"
    All = $true
}
$Hosts = Get-FalconHost @Param
if ($Hosts) {
    $Param = @{
        Name = 'hide_host'
        Ids = $Hosts
    }
    Invoke-FalconHostAction @Param
} else {
    "No hosts found using filter: $Filter"
}
```
## Find duplicate hosts and hide them
**NOTE**: PSFalcon includes a command called `Find-FalconDuplicate` which will analyze the result of a `Get-FalconHost -Detailed` command to find potential duplicates (through grouping by hostname, then sorting by `last_seen` time and selecting all but the most recent).

**WARNING**: `Find-FalconDuplicate` only determines whether or not a device is a "duplicate" by hostname. There may be a legitimate reason that two devices have the same hostname in your environment. It is your responsibility to determine whether or not the hosts reported by `Find-FalconDuplicate` are correct. This script does not provide you with an opportunity to review those hosts before they are hidden, but it does output a list after the hiding is complete. If devices are hidden incorrectly they will continue to communicate with Falcon and can be restored from the trash using their `aid` value and `Invoke-FalconHostAction`.
```powershell
#Requires -Version 5.1 -Modules @{ModuleName="PSFalcon";ModuleVersion='2.0'}
param(
    [switch] $Confirm
)
try {
    # Get detailed information about devices
    $Hosts = Get-FalconHost -Detailed -All

    # Use Find-FalconDuplicate to find duplicate hosts
    if ($Hosts) {
        $Duplicates = Find-FalconDuplicate -Hosts $Hosts
    }
    if ($Duplicates.device_id -and $Confirm) {
        # Output duplicate list to CSV
        $Duplicates | Export-Csv -Path .\duplicates.csv -NoTypeInformation

        # Use Invoke-FalconHostAction to hide hosts
        Invoke-FalconHostAction -Name hide_host -Ids $Duplicates.device_id
    } elseif ($Duplicates) {
        # Output list of duplicates
        Write-Output "Found $($Duplicates.count) potential duplicate hosts"
        Write-Output $Duplicates
    } else {
       Write-Output "No duplicates found."
    }
} catch {
    Write-Error $_
}
```
## Network contain a device by Hostname
```powershell
#Requires -Version 5.1 -Modules @{ModuleName="PSFalcon";ModuleVersion='2.0'}
param(
    [Parameter(Mandatory = $true)]
    [string] $Hostname
)
# Get identifier for target system and choose the most recently seen (in case of duplicates)
$HostId = Get-FalconHost -Filter "hostname:'$Hostname'" -Sort last_seen.desc -Limit 1

if ($HostId) {
    # Contain host
    Invoke-FalconHostAction -Name contain -Ids $HostId
} else {
    throw "No identifier found for '$Hostname'"
}
```
## Network contain a list of Hostnames from a CSV file
**NOTE**: This example requires a CSV with a column labeled `Hostname`. It will create a new CSV with that includes the hostname, device_id and containment request status.
```powershell
#Requires -Version 5.1 -Modules @{ModuleName="PSFalcon";ModuleVersion='2.0'}
param(
    [Parameter(Mandatory = $true)]
    [ValidatePattern('\.csv$')]
    [string] $Path
)
$OutputFile = "Containment_$(Get-Date -Format FileDateTime).csv"
$Hostnames = (Import-Csv $Path).Hostname
$Hosts = for ($i = 0; $i -lt $Hostnames.count; $i += 20) {
    # Retrieve the device_id for hostnames in groups of 20
    $Filter = ($Hostnames[$i..($i + 19)] | ForEach-Object {
        if ($_ -ne '') {
            "hostname:['$_']"
        }
    }) -join ','
    $Output = Get-FalconHost -Filter $Filter -Detailed | Select-Object hostname, device_id
    $Output | ForEach-Object {
        # Add property for each host to update after containment request
        $_.PSObject.Properties.Add((New-Object PSNoteProperty('Contain_Requested', $false)))
    }
    $Output
}
# Contain hosts and add status
Invoke-FalconHostAction -Name contain -Ids $Hosts.device_id | ForEach-Object {
    $Id = $_.id
    ($Hosts | Where-Object { $_.device_id -eq $Id }).Contain_Requested = $true
}
$Hosts | Export-Csv -Path $OutputFile -NoTypeInformation
if (Test-Path $OutputFile) {
    Get-ChildItem $OutputFile
}
```
## Get host information from multiple Falcon instances
**NOTE**: This example requires that you input values for `<client_id>`, `<client_secret>`, and each `<member_cid>`. To avoid hard-coding credentials you could pass them as parameters instead.
```powershell
#Requires -Version 5.1 -Modules @{ModuleName="PSFalcon";ModuleVersion='2.0'}
# ClientId, ClientSecret and MemberCids
$ClientId = '<client_id>'
$ClientSecret = '<client_secret>'
$CIDs = @('<member_cid>', '<member_cid>')

# Enumerate $CIDs
$CIDs | ForEach-Object {
    $Param = @{
        ClientId = $ClientId
        ClientSecret = $ClientSecret
        MemberCid = ($_).ToLower()
    }
    # Authenticate with CID
    Request-FalconToken @Param

    try {
        # Gather and export Host data
        Get-FalconHost -Detailed -All | Export-FalconReport ".\Hosts_for_MemberCid_$($_).csv"
    } catch {
        # Break 'foreach' loop if host retrieval/export fails
        throw $_
    } finally {
        # Remove authentication token and credentials for next CID
        Revoke-FalconToken
    }
}
```
# Host Groups
## Verify that a list of Host Groups exist within child CIDs
```powershell
#Requires -Version 5.1 -Modules @{ModuleName="PSFalcon";ModuleVersion='2.0'}
[CmdletBinding()]
param(
    [Parameter(Mandatory = $true)]
    [ValidatePattern('^\w{32}$')]
    [string] $ClientId,

    [Parameter(Mandatory = $true)]
    [ValidatePattern('^\w{40}$')]
    [string] $ClientSecret,

    [Parameter()]
    [ValidateSet('eu-1', 'us-gov-1', 'us-1', 'us-2')]
    [string] $Cloud,

    [Parameter(Mandatory = $true)]
    [ValidatePattern('^\w{32}$')]
    [array] $MemberCIDs,

    [Parameter(Mandatory = $true)]
    [array] $GroupNames
)
begin {
    # Log file name and output location
    $OutputFile = "VerifyGroup_$(Get-Date -Format FileDateTime).csv"
    $OutputPath = "$(Join-Path -Path ([Environment]::CurrentDirectory) -ChildPath $OutputFile)"
}
process {
    foreach ($CID in $MemberCIDs) {
        $Param = @{
            ClientId = $ClientId
            ClientSecret = $ClientSecret
            MemberCid = ($CID).ToLower()
        }
        if ($Cloud) {
            $Param.Add('Cloud', $Cloud)
        }
        # Authenticate with Member CID
        Request-FalconToken @Param
        try {
            # Get group information
            $Groups = for ($i = 0; $i -lt $GroupNames.count; $i += 20) {
                [array] $NameFilter = ($GroupNames[$i..($i + 19)]).foreach{
                    "name:'$(($_).ToLower())'"
                }
                Get-FalconHostGroup -Filter ($NameFilter -join ',') -Detailed | Select-Object id, name
            }
            # Create output object
            $Output = [PSCustomObject] @{
                CID = $CID
            }
            foreach ($GroupName in $GroupNames) {
                # Add each group name and id
                $IdValue = if ($Groups.name -contains $GroupName) {
                    ($Groups | Where-Object { $_.name -eq $GroupName }).id
                } else {
                    $null
                }
                $Output.PSObject.Properties.Add((New-Object PSNoteProperty($GroupName, $IdValue)))
            }
            # Output to CSV
            $Output | Export-Csv -Path $OutputPath -NoTypeInformation -Append
            Write-Host "Output Host Groups for CID: $CID"
        } catch {
            # Output error and end script
            $_
            break
        } finally {
            # Remove authentication token and credentials for next CID
            Revoke-FalconToken

            # Sleep for 5 seconds to avoid rate limiting on token request
            Start-Sleep -Seconds 5
        }
    }
}
end {
    if (Test-Path -Path $OutputPath) {
        Get-ChildItem -Path $OutputPath
    }
}
```
# Policies
## Modify all Sensor Visibility Exclusions to include an additional Host Group
```powershell
#Requires -Version 5.1 -Modules @{ModuleName="PSFalcon";ModuleVersion='2.0'}
param(
    [Parameter(Mandatory = $true,
        Position = 1)]
    [ValidatePattern('^\w{32}$')]
    [string] $GroupId
)
$SVEs = Get-FalconSVExclusion -Detailed -All
foreach ($SVE in $SVEs) {
    Edit-FalconSVExclusion -Id $SVE.id -GroupIds @($SVE.groups.id, $GroupId)
}
```
## Assign a list of Host Group names to a specific Policy Id within a list of Child CIDs
```powershell
#Requires -Version 5.1 -Modules @{ModuleName="PSFalcon";ModuleVersion='2.0'}
[CmdletBinding()]
param(
    [Parameter(Mandatory = $true)]
    [ValidatePattern('^\w{32}$')]
    [string] $ClientId,

    [Parameter(Mandatory = $true)]
    [ValidatePattern('^\w{40}$')]
    [string] $ClientSecret,

    [Parameter()]
    [ValidateSet('eu-1', 'us-gov-1', 'us-1', 'us-2')]
    [string] $Cloud,

    [Parameter(Mandatory = $true)]
    [ValidatePattern('^\w{32}$')]
    [array] $MemberCIDs,

    [Parameter(Mandatory = $true)]
    [array] $GroupNames,

    [Parameter(Mandatory = $true)]
    [ValidateSet('DeviceControl', 'Firewall', 'Prevention', 'Response', 'SensorUpdate')]
    [string] $PolicyType,

    [Parameter(Mandatory = $true)]
    [ValidatePattern('^\w{32}$')]
    [string] $PolicyId
)
begin {
    # Log file name and output location
    $LogName = "AssignGroup_$(Get-Date -Format FileDateTime).log"
    $LogLocation = "$(Join-Path -Path ([Environment]::CurrentDirectory) -ChildPath $LogName)"

    function Write-LogEntry ([string] $Source, [string] $Message) {
        # Write output and add to log file
        "[$(Get-Date -Format 'yyyy-MM-dd hh:mm:ss') $Source] $Message" | Tee-Object -FilePath $LogLocation -Append
    }
}
process {
    foreach ($CID in $MemberCIDs) {
        $Param = @{
            ClientId = $ClientId
            ClientSecret = $ClientSecret
            MemberCid = ($CID).ToLower()
        }
        if ($Cloud) {
            $Param.Add('Cloud', $Cloud)
        }
        # Authenticate with Member CID
        Request-FalconToken @Param
        try {
            ($GroupNames).foreach{
                # Get Host Group Id
                $GroupId = Get-FalconHostGroup -Filter "name:'$(($_).ToLower())'"
                if ($GroupId) {
                    # Assign Host Group to policy
                    $InvokeCommand = "Invoke-Falcon$($PolicyType)PolicyAction"
                    $Param = @{
                        Name = 'add-host-group'
                        Id = $PolicyId
                        GroupId = $GroupId
                    }
                    $Assigned = & $InvokeCommand @Param
                    if ($Assigned) {
                        $Param = @{
                            Source = $InvokeCommand
                            Message = "Assigned group $($GroupId) to $($PolicyType) policy" +
                                " $($Assigned.id) in CID $($CID)"
                        }
                        Write-LogEntry @Param
                    } else {
                        $Param = @{
                            Source = $InvokeCommand
                            Message = "Failed to assign group $($GroupId) to $($PolicyId) in CID $($CID)"
                        }
                        Write-LogEntry @Param
                    }
                } else {
                    $Param = @{
                        Source = 'Get-FalconHostGroup'
                        Message = "No results for group name '$_' in CID $($CID)"
                    }
                    Write-LogEntry @Param
                }
            }
        } catch {
            # Output error and end script
            $_
            break
        } finally {
            # Remove authentication token and credentials for next CID
            Revoke-FalconToken

            # Sleep for 5 seconds to avoid rate limiting on token request
            Start-Sleep -Seconds 5
        }
    }
}
end {
    if (Test-Path -Path $LogLocation) {
        # Output log file and path
        Get-ChildItem -Path $LogLocation
    }
}
```
## Output a list of assigned Host Groups for designated Policy ids within child CIDs
```powershell
#Requires -Version 5.1 -Modules @{ModuleName="PSFalcon";ModuleVersion='2.0'}
[CmdletBinding()]
param(
    [Parameter(Mandatory = $true)]
    [ValidatePattern('^\w{32}$')]
    [string] $ClientId,

    [Parameter(Mandatory = $true)]
    [ValidatePattern('^\w{40}$')]
    [string] $ClientSecret,

    [Parameter()]
    [ValidateSet('eu-1', 'us-gov-1', 'us-1', 'us-2')]
    [string] $Cloud,

    [Parameter(Mandatory = $true)]
    [ValidatePattern('^\w{32}$')]
    [array] $MemberCIDs,

    [Parameter(Mandatory = $true)]
    [ValidateSet('DeviceControl', 'Firewall', 'Prevention', 'Response', 'SensorUpdate')]
    [string] $PolicyType,

    [Parameter(Mandatory = $true)]
    [ValidatePattern('^\w{32}$')]
    [array] $PolicyIds
)
begin {
    $Filename = "$($PolicyType)PolicyAssignments_$(Get-Date -Format FileDate).csv"
    $OutputPath = "$(Join-Path -Path ([Environment]::CurrentDirectory) -ChildPath $Filename)"
}
process {
    foreach ($CID in $MemberCIDs) {
        $Param = @{
            ClientId = $ClientId
            ClientSecret = $ClientSecret
            MemberCid = ($CID).ToLower()
        }
        if ($Cloud) {
            $Param.Add('Cloud', $Cloud)
        }
        # Authenticate with Member CID
        Request-FalconToken @Param
        try {
            # Get policy information
            $InvokeCommand = "Get-Falcon$($PolicyType)Policy"
            & $InvokeCommand -Ids $PolicyIds | Select-Object id, groups | ForEach-Object {
                [PSCustomObject] @{
                    # Output with CID, policy id and assigned groups
                    CID = $CID
                    PolicyId = "$($_.id)"
                    Groups = $_.groups.id -join ', '
                } | Export-Csv -Path $OutputPath -NoTypeInformation -Append
            }
            Write-Host "Output assigned Host Groups for policies in CID: $CID"
        } catch {
            # Output error and end script
            $_
            break
        } finally {
            # Remove authentication token and credentials for next CID
            Revoke-FalconToken

            # Sleep for 5 seconds to avoid rate limiting on token request
            Start-Sleep -Seconds 5
        }
    }
}
end {
    if (Test-Path -Path $OutputPath) {
        Get-ChildItem -Path $OutputPath
    }
}
```
## Add a list of combined_id exceptions to a Device Control policy
**NOTE**: This script will create 'FULL_ACCESS' exceptions for the 'MASS_STORAGE' class within an existing policy. You can modify the hashtable created in `$Exceptions` to add key/value pairs like `vendor_name` or `product_name`.
```powershell
#Requires -Version 5.1 -Modules @{ModuleName="PSFalcon";ModuleVersion='2.0'}
[CmdletBinding()]
param(
    [Parameter(Mandatory = $true, Position = 1)]
    [ValidatePattern('^\w{32}$')]
    [string] $PolicyId,

    [Parameter(Mandatory = $true, Position = 2)]
    [array] $CombinedIds
)
begin {
    # Maximum number of exceptions to add per request
    $Max = 50
}
process {
    for ($i = 0; $i -lt ($CombinedIds | Measure-Object).Count; $i += $Max) {
        # Create exceptions in groups of $Max
        $IdGroup = $CombinedIds[$i..($i + ($Max - 1))]
        [array] $Exceptions = $IdGroup | ForEach-Object {
            @{
                action = 'FULL_ACCESS'
                combined_id = $_
            }
        }
        $Settings = @{
            classes = @(
                @{
                    id = 'MASS_STORAGE'
                    exceptions = $Exceptions
                }
            )
        }
        Edit-FalconDeviceControlPolicy -Id $PolicyId -Settings $Settings | ForEach-Object {
            # Validate presence of 'combined_id' in policy
            $PolicyExceptions = ($_.settings.classes | Where-Object { $_.id -eq 'MASS_STORAGE' }).exceptions
            ($IdGroup).foreach{
                if ($PolicyExceptions.combined_id -contains $_) {
                    Write-Output "OK: $_"
                }
            }
        }
    }
}
```
# Real-time Response
## Run a command against a group of devices
```powershell
#Requires -Version 5.1 -Modules @{ModuleName="PSFalcon";ModuleVersion='2.0'}
param(
    [Parameter(Mandatory = $true,
        Position = 1)]
    [string] $GroupName,

    [Parameter(Mandatory = $true,
        Position = 2)]
    [string] $Command,

    [Parameter(Position = 3)]
    [string] $Arguments,

    [boolean] $QueueOffline
)
# Find group identifier using 'name' filter
$GroupId = Get-FalconHostGroup -Filter "name:'$($GroupName.ToLower())'"

if ($GroupId) {
    # Get host identifiers for members of $GroupId
    $Members = Get-FalconHostGroupMember -Id $GroupId -All
} else {
    throw "No host group found matching '$GroupName'"
}
if ($Members) {
    # Set filename for CSV export
    $ExportName = "$pwd\rtr_$($Command -replace ' ','_')_$GroupId.csv"

    # Set base parameters for Invoke-FalconRTR
    $Param = @{
        Command = $Command
        HostIds = $Members
    }
    switch ($PSBoundParameters.Keys) {
        # Append parameters from user input that match Invoke-FalconRTR
        { $_ -ne 'GroupName' } {
            $Param[$_] = $PSBoundParameters.$_
        }
    }
    # Issue command and export results to CSV
    Invoke-FalconRTR @Param | Export-Csv -Path $ExportName
    
    if (Test-Path $ExportName) {
        # Display CSV file
        Get-ChildItem $ExportName
    }
} else {
    throw "No members found in host group '$GroupName' [$GroupId]"
}
```
## Upload and execute a local script
**NOTE**: This will get the content of a script from the local administrator computer, encode it (to minimize potential errors due to quotation marks) and run it as a "Raw" script using `Invoke-FalconRTR`.
```powershell
[CmdletBinding()]
param(
    [Parameter(
        Mandatory = $true,
        Position = 1)]
    [ValidateScript({ Test-Path $_ })]
    [string] $Path,

    [Parameter(
        Mandatory = $true,
        Position = 2)]
    [ValidatePattern('^\w{32}$')]
    [array] $HostIds,

    [Parameter(Position = 3)]
    [int] $Timeout
)
begin {
    $EncodedScript = [Convert]::ToBase64String(
        [System.Text.Encoding]::Unicode.GetBytes((Get-Content -Path $Path -Raw)))
}
process {
    $Param = @{
        Command = 'runscript'
        Arguments = '-Raw=```powershell.exe -Enc ' + $EncodedScript + '```'
        HostIds = $HostIds
    }
    if ($HostIds.count -gt 1 -and $Timeout) {
        $Param['Timeout'] = $Timeout
    }
    Invoke-FalconRTR @Param
}
```
## Upload and execute a local script as a secondary process
**NOTE**: Similar to the [other example](https://github.com/CrowdStrike/psfalcon/wiki/Basic-Scripts#upload-and-execute-a-local-script) this will run a script as a secondary PowerShell process on the target device, which helps when scripts are expected to exceed the Real-time Response timeout limit. The downside is that you will not be able to return results from the script unless you write them to a local file on the target host that you access later.
```powershell
[CmdletBinding()]
param(
    [Parameter(
        Mandatory = $true,
        Position = 1)]
    [ValidateScript({ Test-Path $_ })]
    [string] $Path,

    [Parameter(
        Mandatory = $true,
        Position = 2)]
    [ValidatePattern('^\w{32}$')]
    [array] $HostIds,

    [Parameter(Position = 3)]
    [int] $Timeout
)
begin {
    $EncodedScript = [Convert]::ToBase64String(
        [System.Text.Encoding]::Unicode.GetBytes((Get-Content -Path $Path -Raw)))
}
process {
    $Param = @{
        Command = 'runscript'
        Arguments = '-Raw=```Start-Process -FilePath powershell.exe -ArgumentList "-Enc ' + $EncodedScript + '"```'
        HostIds = $HostIds
    }
    if ($HostIds.count -gt 1 -and $Timeout) {
        $Param['Timeout'] = $Timeout
    }
    Invoke-FalconRTR @Param
}
```
# Sensor Installers
## Download the installer package assigned to a Sensor Update policy
```powershell
#Requires -Version 5.1 -Modules @{ModuleName="PSFalcon";ModuleVersion='2.0'}
param(
    [Parameter(Mandatory = $true)]
    [ValidatePattern('^\w{32}$')]
    [string] $PolicyId
)
# Retrieve Sensor Update policy detail
$Policy = Get-FalconSensorUpdatePolicy -Ids $PolicyId -ErrorAction 'SilentlyContinue'

if ($Policy) {
    # Capture OS name and assigned build version
    $PlatformName = $Policy.platform_name.ToLower()
    $BuildVersion = ($Policy.settings.build).Split('|')[0]

    # Get list of available installers for OS
    $Installers = Get-FalconInstaller -Filter "platform:'$PlatformName'" -Detailed
} else {
    throw "No policy found matching '$PolicyId'"
}
if ($Installers) {
    # Select specific installer package matching the Sensor Update policy build version
    $Match = $Installers | Where-Object { $_.version -match "^\d\.\d{1,2}\.$BuildVersion" }

    if ($Match) {
       # Capture SHA256 and output filename
       $InstallerId = $Match.sha256
       $Filename = $Match.name
    }
} else {
    throw "Unable to retrieve installer list; check client permissions"
}
if ($InstallerId -and $Filename) {
    if (Test-Path "$pwd\$Filename") {
        # Check for existing file and compare SHA256 hashes
        $ExistingHash = (Get-FileHash -Algorithm SHA256 -Path "$pwd\$Filename").Hash.ToLower()

        if ($ExistingHash -eq $InstallerId) {
            throw "File already exists [$InstallerId]"
        } 
    }    
    # Download the installer package
    Receive-FalconInstaller -Id $InstallerId -Path "$pwd\$Filename"
} else {
    throw "No sensor installer available matching '$BuildVersion'"
}
```
# Threat Intelligence
## Export domain and IP indicators updated within the last week to CSV
```powershell
#Requires -Version 5.1 -Modules @{ModuleName="PSFalcon";ModuleVersion='2.0'}
$UnixDate = [DateTimeOffset]::Now.AddDays(-7).ToUnixTimeSeconds()
$Param = @{
    Filter = "(type:'ip_address',type:'domain')+last_updated:>$UnixDate"
    Detailed = $true
    All = $true
}
Get-FalconIndicator @Param | Select-Object indicator, type, malicious_confidence, labels | ForEach-Object {
    [PSCustomObject] @{
        value = $_.indicator
        type = $_.type
        confidence = $_.malicious_confidence
        comment = "$(($_.Labels.name | Where-Object { $_ -notmatch 'MaliciousConfidence/*' }) -join ', ')"
    } | Export-Csv -Path .\indicators.csv -NoTypeInformation -Append
}
```
# Vulnerabilities
## Create a report with additional Host fields
```powershell
#Requires -Version 5.1 -Modules @{ModuleName="PSFalcon";ModuleVersion='2.0'}
param(
    [Parameter(Position = 1)]
    [int] $Days = 7,

    [Parameter(Position = 2)]
    [array] $Fields = @('last_seen', 'mac_address', 'serial_number', 'external_ip')
)
if ($Fields -notcontains 'device_id') {
    # Force 'device_id' as a field to be used for matching results
    $Fields += ,'device_id'
}
# Set filename for CSV export
$ExportName = "$pwd\Vulnerabilities_$((Get-Date).AddDays(-$Days).ToString('yyyyMMdd'))_to_$(Get-Date -Format FileDate).csv"

# Gather vulnerabilities within date range (default: last 7 days) and export to CSV
$Param = @{
    Filter = "created_timestamp:>'Last $Days days'"
    Detailed = $true
    All = $true
    Verbose = $true
}
Get-FalconVulnerability @Param | Export-FalconReport -Path $ExportName

if (Test-Path $ExportName) {
    # Import newly created vulnerability report
    $CSV = Import-Csv -Path $ExportName

    # Gather host ids
    $HostIds = ($CSV | Group-Object aid).Name

    # Get detailed information about hosts to append to CSV
    $Param = @{
        Ids = $HostIds
        Verbose = $true
    }
    $HostInfo = Get-FalconHost @Param | Select-Object $Fields

    foreach ($Item in $HostInfo) {
        foreach ($Result in ($CSV | Where-Object { $_.aid -eq $Item.device_id })) {
            foreach ($Property in ($Item.PSObject.Properties | Where-Object { $_.Name -ne 'device_id' })) {
                # Add $Fields from Get-FalconHost, excluding 'device_id' (already present as 'aid')
                $Result.PSObject.Properties.Add((New-Object PSNoteProperty($Property.Name, $Property.Value)))
            }
        }
    }
    # Re-export CSV with added fields
    $CSV | Export-Csv -Path $ExportName -NoTypeInformation -Force
} else {
    throw "No vulnerabilities created within the last $Days days"
}
```
***
The code provided above is for example purposes only and is offered 'as is' with no support.  For specific pieces of code that can help construct scripts, _see [Code Examples](https://github.com/CrowdStrike/psfalcon/wiki/Code-Examples)_.
***