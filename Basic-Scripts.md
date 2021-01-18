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
else {
    # Notify user that detections are being assigned
    Write-Host "Assigning $($Ids.count) detections involving '$Filename' to '$Username'..."

    # Modify detections
    Edit-FalconDetection -Ids $Ids -Status in_progress -AssignedToUuid $Uuid
}
```

# Hosts

### Find duplicate hosts and hide them
```powershell
param(
    [switch] $Confirm
)
$Hosts = Get-FalconHost -Detailed -Limit 5000 -All
$Duplicates = Find-FalconDuplicate -Hosts $Hosts
if ($Duplicates) {
    if ($Confirm) {
        Write-Host "Hiding $($Duplicates.count) potential duplicate hosts..."
        Invoke-FalconHostAction -ActionName hide_host -Ids $Duplicates.device_id
    }
    else {
        Write-Host "Found $($Duplicates.count) potential duplicate hosts"
    }
}
else {
    Write-Host "No duplicates found."
}
```