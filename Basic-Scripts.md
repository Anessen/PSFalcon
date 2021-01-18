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