***
**WARNING**: The code provided below is for example purposes only and is offered 'as is' with no support.
***
# Detections

## Assign detections involving a specific file to a user
```powershell
param(
    [string] $Username,
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
param (
    [string] $Filename
)
do {
    # Gather up to 1,000 detections (maximum for an edit request) involving $Filename
    $Ids = Get-FalconDetection -Filter "behaviors.filename:'$Filename'" -Limit 1000

    if ($Ids) {
        # Export list of ids being hidden
        $Ids | Export-Csv -Path $pwd\hidden_detections.csv -NoTypeInformation -Append -Force

        # Hide group of detections
        Edit-FalconDetection -Ids $Ids -ShowInUi $false

        # Pause to give the API time to clear them out before the next request
        Start-Sleep -Seconds 5
    }
}
while (
    # Exit once no more detections are available
    $Ids
)
```
# Hosts
## Find duplicate hosts and hide them
**NOTE**: PSFalcon includes a command called `Find-FalconDuplicate` which will analyze the result of a `Get-FalconHost -Detailed` command to find potential duplicates (through grouping by hostname, then sorting by `last_seen` time and selecting all but the most recent).
```powershell
param(
    [switch] $Confirm
)
try {
    # Get detailed information about devices
    $Hosts = Get-FalconHost -Detailed -Limit 5000 -All

    # Use Find-FalconDuplicate to find duplicate hosts
    if ($Hosts) {
        $Duplicates = Find-FalconDuplicate -Hosts $Hosts
    }
    if ($Duplicates.device_id -and $Confirm) {
        # Output duplicate list to CSV
        $Duplicates | Export-Csv -Path .\duplicates.csv -NoTypeInformation

        # Use Invoke-FalconHostAction to hide hosts
        Invoke-FalconHostAction -Name hide_host -Ids $Duplicates.device_id
    }
    elseif ($Duplicates) {
        # Output list of duplicates
        Write-Output "Found $($Duplicates.count) potential duplicate hosts"
        Write-Output $Duplicates
    }
    else {
       Write-Output "No duplicates found."
    }
}
catch {
    Write-Error $_
}
```
## Network contain a device by hostname
```powershell
param(
    [string] $Hostname
)
# Get identifier for target system and choose the most recently seen (in case of duplicates)
$HostId = Get-FalconHost -Filter "hostname:'$Hostname'" -Sort last_seen.desc -Limit 1

if ($HostId) {
    # Contain host
    Invoke-FalconHostAction -Name contain -Ids $HostId
}
else {
    throw "No identifier found for '$Hostname'"
}
```
## Get host information from multiple Falcon instances
**NOTE**: This example requires that you input values for `<client_id>`, `<client_secret>`, and each `<member_cid>`. To avoid hard-coding credentials you could pass them as parameters instead.
```powershell
# ClientId, ClientSecret and MemberCids
$ClientId = '<client_id>'
$ClientSecret = '<client_secret>'
$CIDs = @('<member_cid>', '<member_cid>')

# Enumerate $CIDs
$CIDs.foreach{
    $Param = @{
        ClientId = $ClientId
        ClientSecret = $ClientSecret
        MemberCid = ($_).ToLower()
    }
    # Authenticate with CID
    Request-FalconToken @Param

    try {
        # Gather and export Host data
        Get-FalconHost -Limit 5000 -Detailed -All | Export-FalconReport ".\Hosts_for_MemberCid_$($_).csv"
    }
    catch {
        # Break 'foreach' loop if host retrieval/export fails
        throw $_
    }
    finally {
        # Remove authentication token and credentials for next CID
        Revoke-FalconToken
    }
}
```
# Real-time Response
## Run a command against a group of devices
```powershell
param(
    [Parameter(Mandatory = $true)]
    [string] $GroupName,

    [Parameter(Mandatory = $true)]
    [string] $Command,

    [string] $Arguments,

    [boolean] $QueueOffline
)
# Find group identifier using 'name' filter
$GroupId = Get-FalconHostGroup -Filter "name:'$($GroupName.ToLower())'"

if ($GroupId) {
    # Get host identifiers for members of $GroupId
    $Members = Get-FalconHostGroupMember -Id $GroupId -Limit 500 -All
}
else {
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
}
else {
    throw "No members found in host group '$GroupName' [$GroupId]"
}
```
# Sensor Installers
## Download the installer package assigned to a Sensor Update policy
```powershell
param(
    [Parameter(Mandatory = $true)]
    [ValidatePattern('\w{32}')]
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
}
else {
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
}
else {
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
}
else {
    throw "No sensor installer available matching '$BuildVersion'"
}
```
# Threat Intelligence
## Export domain and IP indicators updated within the last week to CSV
```powershell
$UnixDate = [DateTimeOffset]::Now.AddDays(-7).ToUnixTimeSeconds()
$Param = @{
    Filter = "(type:'ip_address',type:'domain')+last_updated:>$UnixDate"
    Limit = 5000
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
param(
    [int] $Days = 7,
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
    Limit = 400
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
}
else {
    throw "No vulnerabilities created within the last $Days days"
}
```
***
**WARNING**: The code provided above is for example purposes only and is offered 'as is' with no support.
***