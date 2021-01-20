***
**WARNING**: The code provided below is for example purposes only and is offered 'as is' with no support.
***
# Detections

## Assign specific detections to a user
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

## Find duplicate hosts and hide them
**NOTE**: PSFalcon includes a command called `Find-FalconDuplicate` which will analyze the result of a `Get-FalconHost -Detailed` command to find potential duplicates (through grouping by hostname, then sorting by `last_seen` time and selecting all but the most recent).
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
**NOTE**: This example requires that you edit `$CIDs` and input values for `<client_id>`, `<client_secret>`, and `<member_cid>` (or `$null` if not required).
```powershell
# Basic structure for storing OAuth2 data for associated CIDs
$CIDs = @(
    @{
        ClientId = '<client_id>'
        ClientSecret = '<client_secret>'
        MemberCid = '<member_cid>'
    },
    @{
        ClientId = '<client_id>'
        ClientSecret = '<client_secret>'
        MemberCid = '<member_cid>'
    }
)
# Enumerate $CIDs
$CIDs.foreach{
    $Param = @{
        ClientId = $_.ClientId
        ClientSecret = $_.ClientSecret
    }
    if ($_.MemberCid) {
        $Param['MemberCid'] = $_.MemberCid
    }
    # Authenticate with CID
    Request-FalconToken @Param

    try {
        # Gather and export Host data
        Get-FalconHost -Limit 5000 -Detailed -All | Export-FalconReport ".\Hosts_for_ClientId_$($_.ClientId).csv"
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
To avoid hardcoding credentials, you could define `$CIDs` outside of the script and modify the example to pass `$CIDs` as a parameter.

If you have a single credential set and multiple member CIDs, you could change the structure of `$CIDs` a bit, and slightly modify the authentication parameters and export filename (unless having them in one CSV works for you).

`$CIDs` structure:
```powershell
$ClientID = '<client_id>'
$ClientSecret = '<client_secret>'
$CIDs = @('<member_cid>', '<member_cid>')
```
Authentication:
```powershell
$Param = @{
    ClientId = $ClientId
    ClientSecret = $ClientSecret
    MemberCid = $_
}
```
Export filename:
```powershell
Get-FalconHost -Limit 5000 -Detailed -All | Export-FalconReport ".\Hosts_for_MemberCid_$($_).csv"
```
***
**WARNING**: The code provided above is for example purposes only and is offered 'as is' with no support.
***