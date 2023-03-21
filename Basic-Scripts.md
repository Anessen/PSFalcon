![CrowdStrike Falcon](https://raw.githubusercontent.com/CrowdStrike/falconpy/main/docs/asset/cs-logo.png)
***
The examples provided below are for example purposes only and are offered 'as is' with no support.
***
### Detections
* [Assign detections involving a specific file to a user](#assign-detections-involving-a-specific-file-to-a-user)
* [Export detections with Custom IOC tags](#export-detections-with-custom-ioc-tags)
* [Hide detections involving a specific file](#hide-detections-involving-a-specific-file)
### Hosts
* [Add a list of hostnames to a host group](#add-a-list-of-hostnames-to-a-host-group)
* [Hide hosts based on last_seen time](#hide-hosts-based-on-last_seen-time)
* [Find duplicate hosts and hide them](#find-duplicate-hosts-and-hide-them)
* [Network contain a device by hostname](#network-contain-a-device-by-hostname)
* [Network contain a list of hostnames from a CSV file](#network-contain-a-list-of-hostnames-from-a-csv-file)
* [Output selected host info and replace ids with names](#output-selected-host-info-and-replace-ids-with-names)
### Host Groups
* [Create a host group and add a list of devices by hostname](#create-a-host-group-and-add-a-list-of-devices-by-hostname)
* [Verify that a list of host groups exist within child CIDs](#verify-that-a-list-of-host-groups-exist-within-child-cids)
### Policies
* [Add a list of combined_id exceptions to a Device Control policy](#add-a-list-of-combined_id-exceptions-to-a-device-control-policy)
* [Assign a list of host group names to a specific policy within a list of child CIDs](#assign-a-list-of-host-group-names-to-a-specific-policy-within-a-list-of-child-cids)
* [Create a list of minimum sensor versions by Linux kernel](#create-a-list-of-minimum-sensor-versions-by-linux-kernel)
* [Create CSVs containing Device Control policy details and exceptions](#create-csvs-containing-device-control-policy-details-and-exceptions)
* [Modify all Sensor Visibility Exclusions to include an additional host group](#modify-all-sensor-visibility-exclusions-to-include-an-additional-host-group)
* [Modify the build of a Sensor Update policy by name](#modify-the-build-of-a-sensor-update-policy-by-name)
* [Output a list of assigned Host Groups for designated Policy ids within child CIDs](#output-a-list-of-assigned-host-groups-for-designated-policy-ids-within-child-cids)
### Real-time Response
* [Download the latest CsWinDiag archive from a list of hosts](#download-the-latest-cswindiag-archive-from-a-list-of-hosts)
* [Execute CsWinDiag and download results from a list of hosts](#execute-cswindiag-and-download-results-from-a-list-of-hosts)
* [Run a command against a group of devices](#run-a-command-against-a-group-of-devices)
* [Upload and execute a local script](#upload-and-execute-a-local-script)
* [Upload and execute a local script as a secondary process](#upload-and-execute-a-local-script)
### Scheduled Reports
* [Download your most recent scheduled report results](#download-your-most-recent-scheduled-report-results)
### Sensor Installers
* [Download the installer package assigned to a Sensor Update policy](#download-the-installer-package-assigned-to-a-sensor-update-policy)
* [Download the installer package assigned to your default Sensor Update policy](#download-the-installer-package-assigned-to-your-default-sensor-update-policy)
### Threat Intelligence
* [Export domain and IP indicators updated within the last week to CSV](#export-domain-and-ip-indicators-updated-within-the-last-week-to-csv)
### Users
* [Create users from CSV](#create-users-from-csv)
### Vulnerabilities
* [Create a report with additional Host fields](#export-domain-and-ip-indicators-updated-within-the-last-week-to-csv)
***
# Detections
## Assign detections involving a specific file to a user
```powershell
#Requires -Version 5.1
using module @{ModuleName='PSFalcon';ModuleVersion='2.2'}
param(
    [Parameter(Mandatory,Position=1)]
    [string]$Username,
    [Parameter(Mandatory,Position=2)]
    [string]$Filename
)
# Get User identifier
$Uuid = Get-FalconUser -Username $Username -EA 0
if (!$Uuid) { throw "No user identifier found for '$Username'." }

if (!(Get-FalconDetection -Filter "behaviors.filename:'$Filename'")) {
    # Generate error if no detections are found for $Filename
    throw "No detections found for '$Filename'."
}
do {
    # Retrieve 1,000 detections that are not assigned and assign them until none are left
    if ($Id) { Start-Sleep -Seconds 5 }
    $Param = @{
        Filter = "behaviors.filename:'$Filename'+assigned_to_uuid:!'$Uuid'"
        Limit = 1000
        OutVariable = 'Id'
    }
    $Edit = Get-FalconDetection @Param | Edit-FalconDetection -AssignedToUuid $Uuid
    if ($Edit.writes.resources_affected) {
        Write-Host ('Assigned {0} detection(s) to {1}...' -f $Edit.writes.resources_affected,$Uuid)
    }
} while ($Id)
```
## Export detections with Custom IOC tags
```powershell
#Requires -Version 5.1
using module @{ModuleName='PSFalcon';ModuleVersion='2.2'}
[string]$OutputFile = Join-Path (Get-Location).Path "custom_ioc_detections_$(Get-Date -Format FileDateTime).json"
try {
    # Retrieve all 'CustomIOC' detections
    [object[]]$Detection = Get-FalconDetection -Filter "behaviors.display_name:*'CustomIOC*'" -Detailed -All
    if ($Detection) {
        # Create search filters for each detected Custom IOC and retrieve type, value, and tags
        [string[]]$Filter = @($Detection.behaviors).foreach{
            "type:'$($_.ioc_type)'+value:'$($_.ioc_value)'"
        } | Select-Object -Unique
        [object[]]$IocList = @($Filter).foreach{
            Get-FalconIoc -Filter $_ -Detailed | Select-Object type,value,tags
        }
        foreach ($Ioc in $IocList) {
            # Append 'ioc_tags' to relevant detection(s)
            ($Detection | Where-Object {
                $_.behaviors.ioc_type -eq $Ioc.type -and $_.behaviors.ioc_value -eq $Ioc.value
            }).behaviors | ForEach-Object {
                $_.PSObject.Properties.Add((New-Object PSNoteProperty('ioc_tags',$Ioc.tags)))
            }
        }
        # Export detections to Json
        $Detection | ConvertTo-Json -Depth 16 >> $OutputFile
        if (Test-Path $OutputFile) { Get-ChildItem $OutputFile | Select-Object FullName,Length,LastWriteTime }
    }
} catch {
    throw $_
}
```
## Hide detections involving a specific file
```powershell
#Requires -Version 5.1
using module @{ModuleName='PSFalcon';ModuleVersion ='2.2'}
param(
    [Parameter(Mandatory)]
    [string]$Filename
)
[string]$OutputFile = Join-Path (Get-Location).Path "hidden_detections_$(Get-Date -Format FileDateTime).txt"
if ($null -eq (Get-FalconDetection -Filter "behaviors.filename:'$Filename'" -Total)) {
    # Generate error if no detections are found for $Filename
    throw "No detections found for '$Filename'."
}
do {
    # Retrieve 1,000 detections and hide them until none are left
    if ($Id) { Start-Sleep -Seconds 5 }
    $Edit = Get-FalconDetection -Filter "behaviors.filename:'$Filename'" -Limit 1000 -OutVariable Id |
        Edit-FalconDetection -ShowInUi $false
    if ($Edit.writes.resources_affected) {
        # Notify of hidden detections and output detection_id values to text file
        Write-Host ('Hid {0} detection(s)...' -f $Edit.writes.resources_affected)
        $Id >> $OutputFile
    }
} while ($Id)
if (Test-Path $OutputFile) { Get-ChildItem $OutputFile | Select-Object FullName,Length,LastWriteTime }
```
# Hosts
## Add a list of hostnames to a host group
**NOTE**: This script expects a text file that contains case-sensitive hostnames (one per line) in `-Path`.
```powershell
#Requires -Version 5.1
using module @{ModuleName='PSFalcon';ModuleVersion ='2.2'}
param(
    [Parameter(Mandatory,Position=1)]
    [ValidatePattern('\.txt$')]
    [ValidateScript({
        if (Test-Path -Path $_ -PathType Leaf) {
            $true
        } else {
            throw "Cannot find path '$_' because it does not exist or is a directory."
        }
    })]
    [string]$Path,
    [Parameter(Mandatory,Position=2)]
    [ValidatePattern('^[a-fA-F0-9]{32}$')]
    [string]$GroupId
)
# Error if host group does not exist
if (!(Get-FalconHostGroup -Id $GroupId)) { throw "No host group found matching '$GroupId'." }

# Use 'Find-FalconHostname' to match list and add hosts to host group
Find-FalconHostname -Path $Path -OutVariable HostList | Invoke-FalconHostGroupAction -Name add-hosts -Id $GroupId

# Error if 'Find-FalconHostname' found no matches
if (!$HostList.hostname) { throw "No hosts found." }
```
## Hide hosts based on last_seen time
```powershell
#Requires -Version 5.1
using module @{ModuleName='PSFalcon';ModuleVersion ='2.2'}
param(
    [Parameter(Mandatory)]
    [ValidateRange(1,44)]
    [int]$Days
)
$Filter = ('last_seen:<{0}' -f "'now-$($Days)d'")
Get-FalconHost -Filter $Filter -All -OutVariable HostList | Invoke-FalconHostAction -Name hide_host
if (!$HostList) { "No hosts found using filter `"$Filter`"." }
```
## Find duplicate hosts and hide them
**WARNING**: `Find-FalconDuplicate` only determines whether or not a device is a "duplicate" by hostname in this
example. There may be a legitimate reason that two devices have the same hostname in your environment. It is your
responsibility to determine whether or not the hosts reported by `Find-FalconDuplicate` are correct. This script
does not provide you with an opportunity to review those hosts before they are hidden, but it does output a list
after the hiding is complete. If devices are hidden incorrectly they will continue to communicate with Falcon
and can be restored from the trash using their `aid` value and `Invoke-FalconHostAction`.
```powershell
#Requires -Version 5.1
using module @{ModuleName='PSFalcon';ModuleVersion ='2.2'}
param(
    [switch]$Confirm
)
[string]$OutputFile = Join-Path (Get-Location).Path "duplicates_$(Get-Date -Format FileDateTime).csv"

# Use Find-FalconDuplicate to find duplicate hosts and hide them
Find-FalconDuplicate -OutVariable Duplicate | Invoke-FalconHostAction -Name hide_host
if ($Duplicate) {
    # If duplicates were found, output to CSV and display file
    $Duplicate | Export-Csv -Path $OutputFile -NoTypeInformation
    if (Test-Path $OutputFile) { Get-ChildItem $OutputFile | Select-Object FullName,Length,LastWriteTime }
}
```
## Network contain a device by hostname
```powershell
#Requires -Version 5.1
using module @{ModuleName='PSFalcon';ModuleVersion ='2.2'}
param(
    [Parameter(Mandatory)]
    [string]$Hostname
)
# Get identifier for target system and choose the most recently seen (in case of duplicates)
Get-FalconHost -Filter "hostname:['$Hostname']" -Sort last_seen.desc -Limit 1 -OutVariable Target |
    Invoke-FalconHostAction -Name contain
if (!$Target) { throw "No identifier found for '$Hostname'." }
```
## Network contain a list of hostnames from a CSV file
**NOTE**: This example requires a CSV with a column labeled `hostname`. It will create a new CSV with that
includes `hostname`, `device_id` and `contain_requested` status.
```powershell
#Requires -Version 5.1
using module @{ModuleName='PSFalcon';ModuleVersion ='2.2'}
param(
    [Parameter(Mandatory)]
    [ValidatePattern('\.csv$')]
    [string]$Path
)
[string]$OutputFile = Join-Path (Get-Location).Path "contained_$(Get-Date -Format FileDateTime).csv"
$Import = Import-Csv -Path $Path
if (!$Import.hostname) { throw "No 'hostname' column found in '$Path'." }

# Use Find-FalconDuplicate to find duplicate hosts and contain them
$Import.hostname | Find-FalconHostname -OutVariable HostList |
    Invoke-FalconHostAction -Name contain -OutVariable ContainList
if (!$HostList.hostname) {
    # Error if no matches were found
    throw "No hosts found."
} else {
    @($HostList).foreach{
        # Add 'contain_requested' property and export to CSV
        $Status = if ($ContainList.id -contains $_.device_id) { $true } else { $false }
        $_.PSObject.Properties.Add((New-Object PSNoteProperty('contain_requested',$Status)))
    }
    $HostList | Export-Csv -Path $OutputFile -NoTypeInformation
    if (Test-Path $OutputFile) { Get-ChildItem $OutputFile | Select-Object FullName,Length,LastWriteTime }
}
```
## Output selected host info and replace ids with names
This script will replace identifiers with the related `name` under each Host result. The fields to include can be
defined under the `Field` variable. The output will be returned in the console.
```powershell
#Requires -Version 5.1
using module @{ModuleName='PSFalcon';ModuleVersion ='2.2'}
# Fields to include with the export to CSV (host group and policy data is automatically added)
[string[]]$Field = 'device_id','hostname','last_seen','first_seen','local_ip','external_ip','agent_version'
$Field += 'device_policies','groups'

# Retrieve all host information and filter to selected fields
$HostInfo = Get-FalconHost -Detailed -All | Select-Object $Field
if ($HostInfo) {
    # Create hashtable to store object detail for hosts
    $Related = @{
        DeviceControlPolicy = @{}
        FirewallPolicy = @{}
        IoaGroup = @{}
        PreventionPolicy = @{}
        ResponsePolicy = @{}
        SensorUpdatePolicy = @{}
        HostGroup = @{}
    }
    foreach ($ItemType in $Related.Keys) {
        # Match policy type to the label used with hosts
        [string]$HostLabel = switch ($ItemType) {
            'DeviceControlPolicy' { 'device_control' }
            'HostGroup' { 'groups' }
            'IoaGroup' { 'rule_groups' }
            'ResponsePolicy' { 'remote_response' }
            'SensorUpdatePolicy' { 'sensor_update' }
            default { ($_ -replace 'Policy', $null).ToLower() }
        }
        [string[]]$Id = if ($ItemType -eq 'IoaGroup') {
            # Collect IOA rule group identifiers
            ($HostInfo.device_policies.prevention.rule_groups | Group-Object).Name
        } elseif ($ItemType -match 'Policy$') {
            # Collect policy identifiers
            ($HostInfo.device_policies.$HostLabel.policy_id | Group-Object).Name
        } else {
            # Collect host group identifiers
            ($HostInfo.groups | Group-Object).Name
        }
        # Collect names and identifiers for each item in hashtable
        [object[]]$Content = & "Get-Falcon$($ItemType)" -Id $Id | Select-Object id,name
        if ($Content) {
            @($Content).foreach{ $Related.$ItemType["$($_.id)"] = "$($_.name)" }
        } else {
            Write-Error "Unable to collect '$ItemType' information. Check permissions."
        }
        @($HostInfo).foreach{
            # Define new property names to add to output
            [string]$Name = if ($ItemType -eq 'HostGroup') {
                'host',$HostLabel -join '_'
            } elseif ($ItemType -eq 'IoaGroup') {
                'ioa',$HostLabel -join '_'
            } else {
                $HostLabel,'policy' -join '_'
            }
            $Value = if ($ItemType -eq 'HostGroup') {
                # Replace host group identifiers with names and remove 'groups'
                if ($_.groups) {
                    ($_.groups | ForEach-Object { $Related.$ItemType.$_ }) -join ','
                    [void]$_.PSObject.Properties.Remove('groups')
                }
            } elseif ($ItemType -eq 'IoaGroup') {
                # Replace IOA rule group identifiers with names
                if ($_.device_policies.prevention.rule_groups) {
                    ($_.device_policies.prevention.rule_groups | ForEach-Object {
                        $Related.$ItemType.$_
                    }) -join ','
                }
            } else {
                # Replace policy identifiers with names and add as '<type>_policy'
                if ($_.device_policies.$HostLabel.policy_id){
                    $Related.$ItemType.($_.device_policies.$HostLabel.policy_id)
                }
            }
            $_.PSObject.Properties.Add((New-Object PSNoteProperty($Name,$Value)))
        }
    }
    # Remove redundant 'device_policies' property
    @($HostInfo).Where({ $_.device_policies }).foreach{ [void]$_.PSObject.Properties.Remove('device_policies') }
    $HostInfo
} else {
    Write-Error "Unable to collect Host information. Check permissions."
}
```
# Host Groups
## Create a host group and add a list of devices by hostname
```powershell
#Requires -Version 5.1
using module @{ModuleName='PSFalcon';ModuleVersion ='2.2'}
param(
    [Parameter(Mandatory,Position=1)]
    [ValidatePattern('\.txt$')]
    [ValidateScript({
        if (Test-Path -Path $_ -PathType Leaf) {
            $true
        } else {
            throw "Cannot find path '$_' because it does not exist or is a directory."
        }
    })]
    [string]$Path,
    [Parameter(Mandatory,Position=2)]
    [string]$Name,
    [Parameter(Position=3)]
    [string]$Description
)
# Create host group
$Param = @{ GroupType = 'static'; Name = $Name }
if ($Description) { $Param['Description'] = $Description }
$Group = New-FalconHostGroup @Param
if (!$Group) { throw "Failed to create host group. Check permissions." }

# Use Find-FalconDuplicate to find hosts and add them to the new group
Find-FalconHostname -Path $Path -OutVariable HostList | Invoke-FalconHostGroupAction -Name add-hosts -Id $Group.id
if (!$HostList) { throw "No hosts found." }
```
## Verify that a list of host groups exist within child CIDs
```powershell
#Requires -Version 5.1
using module @{ModuleName='PSFalcon';ModuleVersion='2.2'}
[CmdletBinding()]
param(
    [Parameter(Mandatory,Position=1)]
    [ValidatePattern('^[a-fA-F0-9]{32}$')]
    [string]$ClientId,
    [Parameter(Mandatory,Position=2)]
    [ValidatePattern('^\w{40}$')]
    [string]$ClientSecret,
    [Parameter(Position=3)]
    [ValidateSet('eu-1','us-gov-1','us-1','us-2')]
    [string]$Cloud,
    [Parameter(Position=4)]
    [ValidatePattern('^[a-fA-F0-9]{32}$')]
    [string[]]$MemberCid,
    [Parameter(Mandatory,Position=5)]
    [string[]]$GroupName
)
begin {
    $Token = @{}
    @('ClientId','ClientSecret','Cloud').foreach{
        if ($PSBoundParameters.$_) { $Token[$_] = $PSBoundParameters.$_ }
    }
    if (!$MemberCid) {
        Request-FalconToken @Token
        if ((Test-FalconToken).Token -eq $true) {
            # Gather available Member CIDs
            [string[]]$MemberCid = Get-FalconMemberCid -Detailed -All | Where-Object {
                $_.status -eq 'active' } | Select-Object -ExpandProperty child_cid
            Revoke-FalconToken
        }
    }
    # Log file name and output location
    [string]$OutputFile = Join-Path (Get-Location).Path "VerifyGroup_$(Get-Date -Format FileDateTime).csv"

}
process {
    foreach ($Cid in $MemberCid) {
        try {
            # Authenticate with Member CID
            Request-FalconToken @Token -MemberCid $Cid
            if ((Test-FalconToken).Token -eq $true) {
                # Get group information
                [object[]]$GroupList = for ($i=0; $i -lt ($GroupName | Measure-Object).Count; $i+=100) {
                    [string]$Filter = (@($GroupName[$i..($i + 99)]).foreach{
                        "name:'$(($_).ToLower())'"
                    }) -join ','
                    Get-FalconHostGroup -Filter $Filter -Detailed | Select-Object id,name
                }
                # Create output object
                $Output = [PSCustomObject]@{ Cid = $Cid }
                foreach ($Name in $GroupName) {
                    # Add each group name and id
                    [string]$Id = if ($GroupList.name -contains $Name) {
                        ($GroupList | Where-Object { $_.name -eq $Name }).id
                    } else {
                        $null
                    }
                    $Output.PSObject.Properties.Add((New-Object PSNoteProperty($Name,$Id)))
                }
                # Output to CSV
                $Output | Export-Csv -Path $OutputFile -NoTypeInformation -Append
                Write-Host "Successfully output host groups for cid '$Cid'."
            }
        } catch {
            Write-Error $_
        } finally {
            if ((Test-FalconToken).Token -eq $true) {
                # Remove authentication token and sleep to avoid rate limiting
                Revoke-FalconToken
                Start-Sleep -Seconds 5
            }
        }
    }
}
end { if (Test-Path $OutputFile) { Get-ChildItem $OutputFile | Select-Object FullName,Length,LastWriteTime }}
```
# Policies
## Add a list of combined_id exceptions to a Device Control policy
**NOTE**: This script will create `FULL_ACCESS` exceptions for the `MASS_STORAGE` class within an existing
policy. You can modify the hashtable created in the `Exception` variable to add key/value pairs like
`vendor_name` or `product_name`.
```powershell
#Requires -Version 5.1
using module @{ModuleName='PSFalcon';ModuleVersion ='2.2'}
param(
    [Parameter(Mandatory,Position=1)]
    [ValidatePattern('^[a-fA-F0-9]{32}$')]
    [string]$PolicyId,
    [Parameter(Mandatory,Position=2)]
    [string[]]$CombinedId
)
# Maximum number of exceptions to add per request
$Max = 50
for ($i=0; $i -lt ($CombinedId | Measure-Object).Count; $i+=$Max) {
    # Create exceptions in groups of $Max
    [string[]]$IdGroup = $CombinedId[$i..($i + ($Max - 1))]
    [object[]]$Exception = @($IdGroup).foreach{ @{ action = 'FULL_ACCESS'; combined_id = $_ }}
    $Setting = [PSCustomObject]@{ classes = @(@{ id = 'MASS_STORAGE'; exceptions = $Exception })}
    @(Edit-FalconDeviceControlPolicy -Id $PolicyId -Setting $Setting).foreach{
        # Validate presence of 'combined_id' in policy
        [object[]]$Created = ($_.settings.classes | Where-Object { $_.id -eq 'MASS_STORAGE' }).exceptions
        @($IdGroup).foreach{ if ($Created.combined_id -contains $_) { Write-Output "Added: $_" }}
    }
}
```
## Assign a list of host group names to a specific policy within a list of child CIDs
```powershell
#Requires -Version 5.1
using module @{ModuleName='PSFalcon';ModuleVersion ='2.2'}
[CmdletBinding()]
param(
    [Parameter(Mandatory,Position=1)]
    [ValidatePattern('^[a-fA-F0-9]{32}$')]
    [string]$ClientId,
    [Parameter(Mandatory,Position=2)]
    [ValidatePattern('^\w{40}$')]
    [string]$ClientSecret,
    [Parameter(Position=3)]
    [ValidatePattern('^[a-fA-F0-9]{32}$')]
    [string[]]$MemberCid,
    [Parameter(Position=4)]
    [ValidateSet('eu-1','us-gov-1','us-1','us-2')]
    [string]$Cloud,
    [Parameter(Mandatory,Position=5)]
    [string[]]$GroupName,
    [Parameter(Mandatory,Position=6)]
    [ValidateSet('DeviceControl','Firewall','Prevention','Response','SensorUpdate')]
    [string]$PolicyType,
    [Parameter(Mandatory,Position=7)]
    [ValidatePattern('^[a-fA-F0-9]{32}$')]
    [string]$PolicyId
)
begin {
    $Token = @{}
    @('ClientId','ClientSecret','Cloud').foreach{
        if ($PSBoundParameters.$_) { $Token[$_] = $PSBoundParameters.$_ }
    }
    if (!$MemberCid) {
        Request-FalconToken @Token
        if ((Test-FalconToken).Token -eq $true) {
            # Gather available Member CIDs
            [string[]]$MemberCid = Get-FalconMemberCid -Detailed -All | Where-Object {
                $_.status -eq 'active' } | Select-Object -ExpandProperty child_cid
            Revoke-FalconToken
        }
    }
    # Log file name and output location
    [string]$OutputFile = Join-Path (Get-Location).Path "AssignGroup_$(Get-Date -Format FileDateTime).log"

    function Write-LogEntry ([string]$Source,[string]$Message) {
        # Write output and add to log file
        "[$(Get-Date -Format 'yyyy-MM-dd hh:mm:ss') $Source] $Message" | Tee-Object -FilePath $OutputFile -Append
    }
}
process {
    foreach ($Cid in $MemberCid) {
        try {
            # Authenticate with Member CID
            Request-FalconToken @Token -MemberCid $Cid
            if ((Test-FalconToken).Token -eq $true) {
                @($GroupName).foreach{
                    # Get Host Group Id
                    $GroupId = Get-FalconHostGroup -Filter "name:'$(($_).ToLower())'"
                    if ($GroupId) {
                        # Assign Host Group to policy
                        $InvokeCommand = "Invoke-Falcon$($PolicyType)PolicyAction"
                        $Param = @{ Name = 'add-host-group'; Id = $PolicyId; GroupId = $GroupId }
                        $Assigned = & $InvokeCommand @Param
                        $Message = if ($Assigned) {
                            "Assigned group $GroupId to $PolicyType policy '$($Assigned.id)' in CID '$Cid'."
                        } else {
                            "Failed to assign group $GroupId to $PolicyType policy '$PolicyId' in CID '$Cid'."
                        }
                        Write-LogEntry $InvokeCommand $Message
                    } else {
                        Write-LogEntry 'Get-FalconHostGroup' "No results for group name '$_' in CID '$Cid'."
                    }
                }
            }
        } catch {
            Write-Error $_
        } finally {
            if ((Test-FalconToken).Token -eq $true) {
                # Remove authentication token and sleep to avoid rate limiting
                Revoke-FalconToken
                Start-Sleep -Seconds 5
            }
        }
    }
}
end { if (Test-Path $OutputFile) { Get-ChildItem $OutputFile | Select-Object FullName,Length,LastWriteTime }}
```
## Create a list of minimum sensor versions by Linux kernel
```powershell
#Requires -Version 5.1
using module @{ModuleName='PSFalcon';ModuleVersion ='2.2'}
<#
.SYNOPSIS
Generate a CSV of minimum supported sensor version by Linux kernel and distro_version
.PARAMETER Path
Path to a text file containing a list of kernels to compare
#>
[CmdletBinding()]
param(
    [Parameter(Mandatory,Position=1)]
    [ValidateScript({
        if (Test-Path $_ -PathType Leaf) {
            $true
        } else {
            throw "Cannot find path '$_' because it does not exist or is not a file."
        }
    })]
    [string]$Path
)
begin {
    [string]$Path = if (![IO.Path]::IsPathRooted($PSBoundParameters.Path)) {
        $FullPath = Join-Path -Path (Get-Location).Path -ChildPath $PSBoundParameters.Path
        $FullPath = Join-Path -Path $FullPath -ChildPath '.'
        [IO.Path]::GetFullPath($FullPath)
    } else {
        $PSBoundParameters.Path
    }
    [string]$OutputFile = Join-Path (Get-Location).Path "KernelSupport_$(Get-Date -Format FileDateTime).csv"
}
process {
    try {
        # Gather list of kernels from text file
        [string[]]$Kernel = Get-Content $Path | Where-Object { ![string]::IsNullOrEmpty($_) }
        if ($Kernel) {
            # Retrieve entire list of supported kernels
            [object[]]$Request = Get-FalconKernel -Limit 500 -All
            if ($Request) {
                # Filter to supported kernels
                [object[]]$Content = $Request | Where-Object { $Kernel -contains $_.release } |
                    Select-Object release,architecture,distro,distro_version,
                    base_package_supported_sensor_versions,ztl_supported_sensor_versions,
                    ztl_module_supported_sensor_versions
                if ($Content) {
                    [System.Collections.Generic.List[object]]$Output = @($Content).foreach{
                        # Create 'minimum_sensor_version' property, using lowest listed version
                        [string]$Minimum = ($_ | Select-Object base_package_supported_sensor_versions,
                        ztl_supported_sensor_versions,ztl_module_supported_sensor_versions
                        ).PSObject.Properties.Value | Group-Object | Sort-Object Name |
                            Select-Object -ExpandProperty Name -First 1
                        [string]$Value = if ($Minimum) { $Minimum } else { 'UNKNOWN' }
                        $_.PSObject.Properties.Add((New-Object PSNoteProperty(
                            'minimum_supported_sensor_version',$Value)))
                        [void]$_.PSObject.Properties.Remove('base_package_supported_sensor_versions')
                        [void]$_.PSObject.Properties.Remove('ztl_supported_sensor_versions')
                        [void]$_.PSObject.Properties.Remove('ztl_module_supported_sensor_versions')
                        $_ | Select-Object release,architecture,distro,distro_version,
                            minimum_supported_sensor_version
                    }
                    @($Kernel).foreach{
                        if ($Output.release -notcontains $_) {
                            $Output.Add([PSCustomObject]@{
                                release = $_
                                architecture = $null
                                distro = $null
                                distro_version = $null
                                minimum_supported_sensor_version = 'NO_MATCH'
                            })
                        }
                    }
                    if (!$Output) { throw 'No results.' }
                    $Output | Export-Csv -Path $OutputFile -NoTypeInformation -Append
                }
            }
        }
    } catch {
        throw $_
    }
}
end { if (Test-Path $OutputFile) { Get-ChildItem $OutputFile | Select-Object FullName,Length,LastWriteTime }}
```
## Create CSVs containing Device Control policy details and exceptions
This script will create a series of CSV files containing information about a given Device Control
policy (settings, members, groups, exceptions, etc.).
```powershell
#Requires -Version 5.1
using module @{ModuleName='PSFalcon';ModuleVersion ='2.2'}
[CmdletBinding(DefaultParameterSetName='Id')]
param(
    [Parameter(ParameterSetName='Id',Mandatory,Position=1)]
    [Parameter(ParameterSetName='Name',Mandatory,Position=1)]
    [ValidatePattern('^[a-fA-F0-9]{32}$')]
    [string]$ClientId,
    [Parameter(ParameterSetName='Id',Mandatory,Position=2)]
    [Parameter(ParameterSetName='Name',Mandatory,Position=2)]
    [ValidatePattern('^\w{40}$')]
    [string]$ClientSecret,
    [Parameter(ParameterSetName='Id',Position=3)]
    [Parameter(ParameterSetName='Name',Position=3)]
    [ValidateSet('eu-1','us-gov-1','us-1','us-2')]
    [string]$Cloud,
    [Parameter(ParameterSetName='Id',Mandatory,Position=4)]
    [ValidatePattern('^[a-fA-F0-9]{32}$')]
    [string]$Id,
    [Parameter(ParameterSetName='Name',Mandatory,Position=5)]
    [string]$Name,
    [Parameter(ParameterSetName='Id',Position=6)]
    [Parameter(ParameterSetName='Name',Position=6)]
    [ValidateScript({
        if ((Test-Path $_) -eq $false) {
            throw "Cannot find path '$_' because it does not exist."
        } elseif ((Test-Path $_ -PathType Container) -eq $false) {
            throw "'Path' must specify a directory."
        } else {
            $true
        }
    })]
    [string]$Path
)
begin {
    function Write-CsvOutput ([object]$Content,[string]$Type) {
        if ($Content) {
            $Param = @{
                Path = Join-Path $OutputFolder "$((Get-Date -Format FileDate),$PolicyId,$Type -join '_').csv"
                NoTypeInformation = $true
                Append = $true
                Force = $true
            }
            $Content | Export-Csv @Param
        }
    }
    [string]$OutputFolder = if (!$Path) { (Get-Location).Path } else { $Path }
    $Token = @{ ClientId = $ClientId; ClientSecret = $ClientSecret }
    if ($Cloud) { $Token['Cloud'] = $Cloud }
    Request-FalconToken @Token
    $VerbosePreference = 'Continue'
}
process {
    [string]$PolicyId = if ((Test-FalconToken).Token -eq $true) {
        if ($Name) {
            try {
                Get-FalconDeviceControlPolicy -Filter "name:'$($Name.ToLower())'"
            } catch {
                throw "No Device Control policy found matching '$($Name.ToLower())'."
            }
        } else {
            $Id
        }
    }
    if ($PolicyId) {
        foreach ($Item in (Get-FalconDeviceControlPolicy -Id $PolicyId)) {
            $Item.settings.PSObject.Members.Where({ $_.MemberType -eq 'NoteProperty' }).foreach{
                if ($_.Name -eq 'classes') {
                    Write-CsvOutput ($_.Value | Select-Object id,action) 'classes'
                    foreach ($Exception in ($_.Value).Where({ $_.exceptions }).exceptions) {
                        Write-CsvOutput $Exception 'exceptions'
                    }
                } else {
                    $Item.PSObject.Properties.Add((New-Object PSNoteProperty($_.Name,$_.Value)))
                }
            }
            foreach ($Property in @('groups','settings')) {
                if ($Item.$Property -and $Property -eq 'groups') {
                    Write-CsvOutput ($Item.$Property | Select-Object id,name) $Property
                }
                $Item.PSObject.Properties.Remove($Property)
            }
            Write-CsvOutput $Item 'settings'
            Write-CsvOutput (Get-FalconDeviceControlPolicyMember -Id $PolicyId -Detailed -All |
                Select-Object device_id,hostname) 'members'
        }
    }
}
end { if (Test-Path $OutputFolder) { Get-ChildItem $OutputFolder | Select-Object FullName,Length,LastWriteTime }}
```
## Modify all Sensor Visibility Exclusions to include an additional host group
```powershell
#Requires -Version 5.1
using module @{ModuleName='PSFalcon';ModuleVersion='2.2'}
param(
    [Parameter(Mandatory,Position=1)]
    [ValidatePattern('^[a-fA-F0-9]{32}$')]
    [string]$GroupId
)
Get-FalconSvExclusion -Detailed -All | ForEach-Object {
    Edit-FalconSvExclusion -Id $_.id -GroupId @($_.groups.id,$GroupId)
}
```
### Modify the build of a Sensor Update policy by name
```powershell
#Requires -Version 5.1
using module @{ModuleName='PSFalcon';ModuleVersion ='2.2'}
param(
    [Parameter(Mandatory,Position=1)]
    [string]$Name,
    [Parameter(Mandatory,Position=2)]
    [string]$Version
)
[string]$Id = Get-FalconSensorUpdatePolicy -Filter "name.raw:'$Name'"
if (!$Id) { throw "No policy found matching '$Name'." }
if ($Version -match '\.') { $Version = [string]($Version -split '\.')[-1] }
if ((Get-FalconBuild).build -notcontains $Version) { throw "'$Version' is not a valid build number." }
Edit-FalconSensorUpdatePolicy -Id $Id -Setting @{ build = $Version } | Select-Object id,name,@{Label='build';
    Expression={$_.settings.build}}
```
## Output a list of assigned Host Groups for designated Policy ids within child CIDs
```powershell
#Requires -Version 5.1
using module @{ModuleName='PSFalcon';ModuleVersion ='2.2'}
[CmdletBinding()]
param(
    [Parameter(Mandatory,Position=1)]
    [ValidatePattern('^[a-fA-F0-9]{32}$')]
    [string]$ClientId,
    [Parameter(Mandatory,Position=2)]
    [ValidatePattern('^\w{40}$')]
    [string]$ClientSecret,
    [Parameter(Mandatory,Position=3)]
    [ValidatePattern('^[a-fA-F0-9]{32}$')]
    [string[]]$MemberCid,
    [Parameter(Position=4)]
    [ValidateSet('eu-1','us-gov-1','us-1','us-2')]
    [string]$Cloud,
    [Parameter(Mandatory,Position=5)]
    [ValidateSet('DeviceControl','Firewall','Prevention','Response','SensorUpdate')]
    [string]$PolicyType,
    [Parameter(Mandatory,Position=6)]
    [ValidatePattern('^[a-fA-F0-9]{32}$')]
    [string[]]$PolicyId
)
begin {
    $Token = @{}
    @('ClientId','ClientSecret','Cloud').foreach{
        if ($PSBoundParameters.$_) { $Token[$_] = $PSBoundParameters.$_ }
    }
    if (!$MemberCid) {
        Request-FalconToken @Token
        if ((Test-FalconToken).Token -eq $true) {
            # Gather available Member CIDs
            [string[]]$MemberCid = Get-FalconMemberCid -Detailed -All | Where-Object {
                $_.status -eq 'active' } | Select-Object -ExpandProperty child_cid
            Revoke-FalconToken
        }
    }
    [string]$OutputFile = Join-Path (Get-Location).Path "$(
        $PolicyType)Assignment_$(Get-Date -Format FileDate).csv"
}
process {
    foreach ($Cid in $MemberCid) {
        try {
            # Authenticate with Member CID
            Request-FalconToken @Token -MemberCid $Cid
            if ((Test-FalconToken).Token -eq $true) {
                # Get policy information
                & "Get-Falcon$($PolicyType)Policy" -Id $PolicyId | Select-Object id,groups | ForEach-Object {
                    [PSCustomObject]@{
                        # Output with CID, policy id and assigned groups
                        Cid = $Cid
                        PolicyId = $_.id
                        Groups = $_.groups.id -join ', '
                    } | Export-Csv -Path $OutputFile -NoTypeInformation -Append
                }
                Write-Host "Output assigned host groups for CID '$Cid'."
            }
        } catch {
            Write-Error $_
        } finally {
            if ((Test-FalconToken).Token -eq $true) {
                # Remove authentication token and sleep to avoid rate limiting
                Revoke-FalconToken
                Start-Sleep -Seconds 5
            }
        }
    }
}
end { if (Test-Path $OutputFile) { Get-ChildItem $OutputFile | Select-Object FullName,Length,LastWriteTime }}
```
# Real-time Response
## Download the latest CsWinDiag archive from a list of hosts
```powershell
#Requires -Version 5.1
using module @{ModuleName='PSFalcon';ModuleVersion ='2.2'}
[CmdletBinding()]
param(
    [Parameter(Mandatory=$true,Position=1)]
    [ValidatePattern('^[a-fA-F0-9]{32}$')]
    [string[]]$HostId
)
begin {
    # Script to check for latest 'cswindiag' archive
    [string]$CheckDiag = 'Get-ChildItem -Path (Join-Path $env:ProgramFiles "CrowdStrike\Rtr\PutRun") -Filter "CS' +
        'WinDiag*.zip" | Select-Object -First 1 -ExpandProperty FullName'
}
process {
    try {
        # Filter to Windows hosts
        [string[]]$HostList = $HostId | Select-Object -Unique | Get-FalconHost | Where-Object {
            $_.platform_name -eq 'Windows' } | Select-Object -ExpandProperty device_id
        if ($HostId -and !$HostList) { throw "'CsWinDiag' is only available for Windows hosts." }
        [string]$Argument = '-Raw=```' + $CheckDiag + '```'
        $GetList = $HostList | Invoke-FalconRtr -Command runscript -Argument $Argument | ForEach-Object {
            if ($_.stdout) {
                # If CsWinDiag present, issue 'get' command
                Write-Host "Issuing 'get' for '$($_.stdout | Split-Path -Leaf)' on host '$($_.aid)'..."
                Invoke-FalconRtr -Command get -Argument "'$($_.stdout)'" -HostId $_.aid
            } else {
                Write-Warning "No 'cswindiag' package found for host '$($_.aid)'."
            }
        }
        if ($GetList) {
            @($GetList).foreach{
                $_ | Confirm-FalconGetFile | ForEach-Object {
                    if ($_.sha256) {
                        # If download complete, and file does not exist, download file
                        [string]$File = Join-Path (Get-Location).Path "$($_.name | Split-Path -Leaf).7z"
                        if ((Test-Path $File) -eq $false) {
                            Write-Host "Downloading '$($_.name | Split-Path -Leaf)' from host '$($_.aid)'..."
                            $_ | Receive-FalconGetFile -Path $File
                        }
                    } else {
                        Write-Warning "'get' incomplete for host '$($_.aid)'."
                    }
                }
            }
        }
    } catch {
        throw $_
    }
}
```
## Execute CsWinDiag and download results from a list of hosts
```powershell
#Requires -Version 5.1
using module @{ModuleName='PSFalcon';ModuleVersion ='2.2'}
[CmdletBinding()]
param(
    [Parameter(Mandatory=$true,Position=1)]
    [ValidatePattern('^[a-fA-F0-9]{32}$')]
    [string[]]$HostId
)
begin {
    # Script to check for newly created 'cswindiag' archives
    [string]$CheckDiag = '$CsWinDiag = Get-ChildItem -Path (Join-Path $env:ProgramFiles "CrowdStrike\Rtr\PutRun"' +
        ') -Filter "CSWinDiag*.zip" | Where-Object { $_.LastWriteTime.Ticks -gt {0} } | Select-Object -First 1 |' +
        'Select-Object -ExpandProperty FullName; if ($CsWinDiag) { $CsWinDiag } else { throw "incomplete" }'
}
process {
    try {
        # Filter to Windows hosts
        [string[]]$HostList = $HostId | Select-Object -Unique | Get-FalconHost | Where-Object {
            $_.platform_name -eq 'Windows' } | Select-Object -ExpandProperty device_id
        if ($HostId -and !$HostList) { throw "'CsWinDiag' is only available for Windows hosts." }
        # Create variables to track results
        [System.Collections.Generic.List[string]]$WaitDiag = @()
        @('DiagCreated','Failed','WaitGet').foreach{
            New-Variable -Name $_ -Value ([System.Collections.Generic.List[PSCustomObject]]@())
        }
        # Start batch session
        Write-Host "Starting batch Real-time Response session with $(
            ($HostList | Measure-Object).Count) host(s)..."
        $Batch = Start-FalconSession -Id $HostList -Timeout 60
        if (!$Batch.batch_id) { throw "Failed to create batch Real-time Response session." }
        # Issue 'cswindiag' command
        $Start = (Get-Date).Ticks
        $Cmd = $Batch | Invoke-FalconAdminCommand -Command cswindiag
        foreach ($CmdResult in $Cmd) {
            if ($CmdResult.stdout -eq 'The process was successfully started') {
                $WaitDiag.Add($CmdResult.aid)
            } else {
                $Failed.Add($CmdResult)
            }
        }
        if ($WaitDiag.Count -gt 0) {
            Write-Host "Started 'cswindiag' on $($WaitDiag.Count) host(s). Waiting for result(s)..."
            [string]$Argument = '-Raw=```' + ($CheckDiag -replace '\{0\}',$Start) + '```'
            do {
                # Check each host for diagnostic archive created after $Start
                Start-Sleep -Seconds 30
                $Param = @{
                    BatchId = $Batch.batch_id
                    Command = 'runscript'
                    Argument = $Argument
                    OptionalHostId = $WaitDiag
                }
                $Cmd = Invoke-FalconAdminCommand @Param
                foreach ($ScriptResult in ($Cmd | Where-Object { $_.stdout })) {
                    # When archive is created, gather aid and path to archive
                    Write-Host "Result created for host '$($ScriptResult.aid)'."
                    $DiagCreated.Add($ScriptResult)
                    [void]$WaitDiag.Remove($ScriptResult.aid)
                }
                if ($WaitDiag.Count -gt 0) {
                    Write-Host "Waiting for result(s)... [$(($DiagCreated.Count/($DiagCreated.Count +
                        $WaitDiag.Count)).ToString("P")) complete]"
                }
            } until ( $WaitDiag.Count -eq 0 )
            if ($DiagCreated -eq 0) { throw "No 'cswindiag' result(s) created." }
            foreach ($FileResult in $DiagCreated) {
                # Issue 'get' for each archive on each host
                Write-Host "Issuing 'get' for host '$($FileResult.aid)'..."
                $Param = @{
                    BatchId = $Batch.batch_id
                    FilePath = "'$($FileResult.stdout)'"
                    OptionalHostId = $FileResult.aid
                }
                (Invoke-FalconBatchGet @Param).hosts | ForEach-Object { $WaitGet.Add($_) }
            }
            if ($WaitGet -eq 0) { throw "No 'get' commands successfully issued." }
            do {
                $ConfirmHost = $WaitGet | Where-Object { $null -ne $_.stdout -and $_.complete -eq $true }
                if ($null -ne $ConfirmHost) {
                    # Check 'get' results every 30 seconds
                    Write-Host "Waiting for upload(s)... [$((($ConfirmHost |
                        Measure-Object).Count/$WaitGet.Count).ToString("P")) complete]"
                    Start-Sleep -Seconds 30
                    foreach ($Item in $ConfirmHost) {
                        $Item | Confirm-FalconGetFile | ForEach-Object {
                            if ($_.sha256) {
                                # Receive diagnostic
                                $_ | Receive-FalconGetFile -Path "$($_.name | Split-Path -Leaf).7z"
                                ($WaitGet | Where-Object { $_.session_id -eq $Item.session_id }) | ForEach-Object {
                                    # Remove 'stdout' to exclude from further processing
                                    $_.stdout = $null
                                }
                            }
                        }
                    }
                }
            } until ( $null -eq $ConfirmHost )
        }
        # Output failures
        if ($Failed.Count -gt 0) { $Failed }
    } catch {
        throw $_
    }
}
```
## Run a command against a group of devices
```powershell
#Requires -Version 5.1
using module @{ModuleName='PSFalcon';ModuleVersion ='2.2'}
param(
    [Parameter(Mandatory,Position=1)]
    [string]$GroupName,
    [Parameter(Mandatory,Position=2)]
    [string]$Command,
    [Parameter(Position=3)]
    [string]$Arguments,
    [boolean]$QueueOffline
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
    $ExportName = Join-Path (Get-Location).Path "$('rtr',($Command -replace ' ','_'),$GroupId -join '_').csv"

    # Set base parameters for Invoke-FalconRTR
    $Param = @{ Command = $Command; HostId = $Members }
    switch ($PSBoundParameters.Keys) {
        # Append parameters from user input that match Invoke-FalconRTR
        { $_ -ne 'GroupName' } { $Param[$_] = $PSBoundParameters.$_ }
    }
    # Issue command and export results to CSV
    Invoke-FalconRtr @Param | Export-Csv -Path $ExportName
    
    if (Test-Path $ExportName) {
        # Display CSV file
        Get-ChildItem $ExportName
    }
} else {
    throw "No members found in host group '$GroupName' [$GroupId]"
}
```
## Upload and execute a local script
**NOTE**: This will get the content of a script from the local administrator computer, encode it (to minimize
potential errors due to quotation marks) and run it as a "Raw" script using `Invoke-FalconRtr`.
```powershell
[CmdletBinding()]
param(
    [Parameter(Mandatory,Position=1)]
    [ValidateScript({ Test-Path $_ })]
    [string]$Path,
    [Parameter(Mandatory,Position=2)]
    [ValidatePattern('^[a-fA-F0-9]{32}$')]
    [string[]]$HostId,
    [Parameter(Position=3)]
    [int]$Timeout
)
begin {
    $EncodedScript = [Convert]::ToBase64String(
        [System.Text.Encoding]::Unicode.GetBytes((Get-Content -Path $Path -Raw)))
}
process {
    $Param = @{
        Command = 'runscript'
        Arguments = '-Raw=```powershell.exe -Enc ' + $EncodedScript + '```'
        HostId = $HostId
    }
    if ($HostId.count -gt 1 -and $Timeout) { $Param['Timeout'] = $Timeout }
    Invoke-FalconRtr @Param
}
```
## Upload and execute a local script as a secondary process
**NOTE**: Similar to the [other example](#upload-and-execute-a-local-script) this will run a script as a secondary
PowerShell process on the target device, which helps when scripts are expected to exceed the Real-time Response
timeout limit. The downside is that you will not be able to return results from the script unless you write them
to a local file on the target host that you access later.
```powershell
[CmdletBinding()]
param(
    [Parameter(Mandatory,Position=1)]
    [ValidateScript({ Test-Path $_ })]
    [string]$Path,
    [Parameter(Mandatory,Position=2)]
    [ValidatePattern('^[a-fA-F0-9]{32}$')]
    [string[]]$HostId,
    [Parameter(Position=3)]
    [int]$Timeout
)
begin {
    $EncodedScript = [Convert]::ToBase64String(
        [System.Text.Encoding]::Unicode.GetBytes((Get-Content -Path $Path -Raw)))
}
process {
    $Param = @{
        Command = 'runscript'
        Arguments = '-Raw=```Start-Process -FilePath powershell.exe -ArgumentList "-Enc ' + $EncodedScript + '"```'
        HostId = $HostId
    }
    if ($HostIds.count -gt 1 -and $Timeout) { $Param['Timeout'] = $Timeout }
    Invoke-FalconRtr @Param
}
```
# Scheduled Reports
## Download your most recent scheduled report results
This is a simple one-line script that will download the most recent scheduled report results into your current
directory.
```powershell
#Requires -Version 5.1
using module @{ModuleName='PSFalcon';ModuleVersion ='2.2'}
(Get-FalconScheduledReport -Detailed -All).last_execution | ForEach-Object {
    Receive-FalconScheduledReport -Id $_.id -Path "$($_.result_metadata.report_file_name)"
}
```
# Sensor Installers
## Download the installer package assigned to a Sensor Update policy
```powershell
#Requires -Version 5.1
using module @{ModuleName='PSFalcon';ModuleVersion ='2.2'}
param(
    [Parameter(Mandatory)]
    [ValidatePattern('^[a-fA-F0-9]{32}$')]
    [string]$PolicyId
)
try {
    # Retrieve Sensor Update policy detail
    $Policy = Get-FalconSensorUpdatePolicy -Id $PolicyId
    if ($Policy.platform_name -and $Policy.settings) {
        # Use build and sensor_version to create regex pattern
        [regex]$Pattern = "^($([regex]::Escape(
            ($Policy.settings.sensor_version -replace '\.\d+$',$null)))\.\d{1,}|\d\.\d{1,}\.$(
            $Policy.settings.build.Split('|')[0]))$"
        $Match = try {
            # Select matching installer from list for 'platform_name' using regex pattern
            Get-FalconInstaller -Filter "platform:'$($Policy.platform_name.ToLower())'" -Detailed |
                Where-Object { $_.version -match $Pattern -and $_.description -match 'Falcon Sensor' }
        } catch {
            throw 'Unable to find installer through version match'
        }
        if ($Match.sha256 -and $Match.name) {
            $Installer = Join-Path -Path (Get-Location).Path -ChildPath $Match.name
            if ((Test-Path $Installer) -and ((Get-FileHash -Algorithm SHA256 -Path $Installer) -eq $Match.sha256)) {
                # Abort if matching file already exists
                throw "File exists with matching hash [$($Match.sha256)]"
            } elseif (Test-Path $Installer) {
                # Remove other versions
                Remove-Item -Path $Installer -Force
            }
            # Download the installer package
            Receive-FalconInstaller -Id $Match.sha256 -Path $Installer
        } else {
            throw "Properties 'sha256' or 'name' missing from installer result"
        }
    }
} catch {
    throw $_
}
```
## Download the installer package assigned to your default Sensor Update policy
```powershell
#Requires -Version 5.1
using module @{ModuleName='PSFalcon';ModuleVersion ='2.2'}
[CmdletBinding()]
param(
    [Parameter(Mandatory,Position=1)]
    [ValidateScript({
        if (Test-Path -Path $_ -PathType Container) {
            $true
        } else {
            throw "Cannot find path '$_' because it does not exist or is not a directory."
        }
    })]
    [string]$Path
)
begin {
    # Ensure absolute path for output directory
    $OutputDirectory = if (![IO.Path]::IsPathRooted($PSBoundParameters.Path)) {
        $FullPath = Join-Path -Path (Get-Location).Path -ChildPath $PSBoundParameters.Path
        $FullPath = Join-Path -Path $FullPath -ChildPath '.'
        [IO.Path]::GetFullPath($FullPath)
    } else {
        $PSBoundParameters.Path
    }
}
process {
    try {
        # Retrieve Sensor Update policy detail
        $Policy = Get-FalconSensorUpdatePolicy -Filter "platform_name:'Windows'+name:'platform_default'" -Detailed
        if ($Policy.platform_name -and $Policy.settings) {
            # Use build and sensor_version to create regex pattern
            [regex]$Pattern = "^($([regex]::Escape(
                ($Policy.settings.sensor_version -replace '\.\d+$',$null)))\.\d{1,}|\d\.\d{1,}\.$(
                $Policy.settings.build.Split('|')[0]))$"
            $Match = try {
                # Select matching installer from list for 'platform_name' using regex pattern
                Get-FalconInstaller -Filter "platform:'$($Policy.platform_name.ToLower())'" -Detailed |
                    Where-Object { $_.version -match $Pattern -and $_.description -match 'Falcon Sensor' }
            } catch {
                throw 'Unable to find installer through version match'
            }
            if ($Match.sha256 -and $Match.name) {
                $Installer = Join-Path -Path $OutputDirectory -ChildPath $Match.name
                if ((Test-Path $Installer) -and ((Get-FileHash -Algorithm SHA256 -Path $Installer) -eq
                $Match.sha256)) {
                    # Abort if matching file already exists
                    throw "File exists with matching hash [$($Match.sha256)]"
                } elseif (Test-Path $Installer) {
                    # Remove other versions
                    Remove-Item -Path $Installer -Force
                }
                # Download the installer package
                $Receive = Receive-FalconInstaller -Id $Match.sha256 -Path $Installer
                if (Test-Path $Receive.FullName) {
                    $Match | ForEach-Object {
                        # Output installer information with 'file_path' of local file
                        $_.PSObject.Properties.Add((New-Object PSNoteProperty('file_path',$Receive.FullName)))
                        $_
                    }
                } else {
                    throw "Installer download failed. [$($Match.sha256)]"
                }
            } else {
                throw "Properties 'sha256' or 'name' missing from installer result."
            }
        } else {
            throw "Unable to retrieve default policy for Windows."
        }
    } catch {
        throw $_
    }
}
```
# Threat Intelligence
## Export domain and IP indicators updated within the last week to CSV
```powershell
#Requires -Version 5.1
using module @{ModuleName='PSFalcon';ModuleVersion ='2.2'}
$UnixDate = [DateTimeOffset]::Now.AddDays(-7).ToUnixTimeSeconds()
$Param = @{
    Filter = "(type:'ip_address',type:'domain')+last_updated:>$UnixDate"
    Detailed = $true
    All = $true
}
Get-FalconIndicator @Param | Select-Object indicator,type,malicious_confidence,labels | ForEach-Object {
    [PSCustomObject]@{
        value = $_.indicator
        type = $_.type
        confidence = $_.malicious_confidence
        comment = "$(($_.Labels.name | Where-Object { $_ -notmatch 'MaliciousConfidence/*' }) -join ', ')"
    } | Export-Csv -Path .\indicators.csv -NoTypeInformation -Append
}
```
# Users
## Create users from CSV
```powershell
#Requires -Version 5.1
using module @{ModuleName='PSFalcon';ModuleVersion ='2.2'}
param(
    [Parameter(Mandatory,Position=1)]
    [ValidateSet('https://api.crowdstrike.com','https://api.us-2.crowdstrike.com',
        'https://api.laggar.gcw.crowdstrike.com','https://api.eu-1.crowdstrike.com')]
    [string]$BaseAddress,
    [Parameter(Mandatory,Position=2)]
    [ValidatePattern('^[a-fA-F0-9]{32}$')]
    [string]$ClientId,
    [Parameter(Mandatory,Position=3)]
    [ValidatePattern('^\w{40}$')]
    [string]$ClientSecret,
    [Parameter(Position=4)]
    [ValidatePattern('^[a-fA-F0-9]{32}$')]
    [string]$MemberCid,
    [Parameter(Mandatory,Position=5)]
    [ValidatePattern('\.csv$')]
    [ValidateScript({ Test-Path $_ })]
    [string]$Path
)
$Param = @{
    Hostname = $BaseAddress
    ClientId = $ClientId
    ClientSecret = $ClientSecret
}
if ($MemberCid) { $Param['MemberCid'] = $MemberCid }
Request-FalconToken @Param
if ((Test-FalconToken).Token -eq $true) {
    $CSV = Import-Csv $Path
    @($CSV).foreach{
        @($_.PSObject.Properties.Name).foreach{
            if ($_ -notmatch '^(Email|Firstname|Lastname|Roles)$') {
                # Error if invalid columns exist
                throw "Unexpected column. Ensure 'Email', 'Firstname', 'Lastname' and 'Roles' are present. ['$_']"
            }
        }
        if ($_.Roles) {
            # Convert Roles into an [array]
            $_.Roles = ($_.Roles -Split ',').Trim()
        }
    }
    if ($CSV.Roles -and $CSV.Roles -match '\s') {
        # Replace 'Display Names' (from console output) with role IDs
        $Roles = Get-FalconRole -Detailed
        if ($Roles) {
            @($CSV).foreach{
                $_.Roles = @($_.Roles).foreach{
                    $_ -replace $_,($Roles | Where-Object display_name -eq $_).id
                }
            }
        }
    }
    $CSV | ForEach-Object {
        # Create user
        $User = New-FalconUser -Username $_.Email -Firstname $_.Firstname -Lastname $_.Lastname
        if ($User.uuid -and $_.Roles) {
            # Assign roles
            Add-FalconRole -UserId $User.uuid -Id $_.Roles
        } elseif ($User.uuid) {
            # Assign 'falcon_console_guest' if roles are not present
            Add-FalconRole -UserId $User.uuid -Id falcon_console_guest
        }
    }
}
```
# Vulnerabilities
## Create a report with additional Host fields
```powershell
#Requires -Version 5.1
using module @{ModuleName='PSFalcon';ModuleVersion ='2.2'}
param(
    [Parameter(Position=1)]
    [int]$Days = 7,
    [Parameter(Position=2)]
    [string[]]$Fields = @('last_seen','mac_address','serial_number','external_ip')
)
# Force 'device_id' as a field to be used for matching results and set export filename
if ($Fields -notcontains 'device_id') { $Fields += ,'device_id' }
$ExportName = Join-Path (Get-Location).Path "Vulnerabilities_$(
    (Get-Date).AddDays(-$Days).ToString('yyyyMMdd'))_to_$(Get-Date -Format FileDate).csv"

# Gather vulnerabilities within date range (default: last 7 days) and export to CSV
$Param = @{
    Filter = "created_timestamp:>'last $Days days'"
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
    $Param = @{ Id = $HostIds; Verbose = $true }
    $HostInfo = Get-FalconHost @Param | Select-Object $Fields

    foreach ($Item in $HostInfo) {
        foreach ($Result in ($CSV | Where-Object { $_.aid -eq $Item.device_id })) {
            foreach ($Property in ($Item.PSObject.Properties | Where-Object { $_.Name -ne 'device_id' })) {
                # Add $Fields from Get-FalconHost, excluding 'device_id' (already present as 'aid')
                $Result.PSObject.Properties.Add((New-Object PSNoteProperty($Property.Name,$Property.Value)))
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
The examples provided above are for example purposes only and are offered 'as is' with no support.
***