## Managing CID Groups
### List CID groups by ID
```powershell
Get-FalconCIDGroup [-Detailed] [-All]
```
### Retrieve detail about one or more CID groups
```powershell
Get-FalconCIDGroup -Ids <id>, <id>
```
### Create a CID group
```powershell
New-FalconCIDGroup -Name 'Manual Testing' -Description 'Manual Testing'
```
### Update a CID group
```powershell
Edit-FalconCIDGroup -Id <id> -Name 'Updated Name' -Description 'Updated name for manual testing'
```
### Delete a CID group
```powershell
Remove-FalconCIDGroup -Ids <id>, <id>
```
_See CrowdStrike API Documentation[]()._