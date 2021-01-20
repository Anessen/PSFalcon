**WARNING**: The code provided below is for example purposes only. These scripts are offered 'as is' with no support.

# Detections

### Assign specific detections to a user
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

# Hosts

### Find duplicate hosts and hide them
```powershell
param(
    [switch] $Confirm
)
# Get detailed information about devices
$Hosts = Get-FalconHost -Detailed -Limit 5000 -All

# Use Find-FalconDuplicate to find duplicate hosts
$Duplicates = Find-FalconDuplicate -Hosts $Hosts

if ($Duplicates) {
    if ($Confirm) {
        # Notify user
        Write-Host "Hiding $($Duplicates.count) potential duplicate hosts..."

        # Use Invoke-FalconHostAction to hide hosts
        Invoke-FalconHostAction -Name hide_host -Ids $Duplicates.device_id
    }
    else {
        # Notify user of duplicates
        Write-Host "Found $($Duplicates.count) potential duplicate hosts"
    }
}
else {
    Write-Host "No duplicates found."
}
```

### Network contain a device by hostname
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