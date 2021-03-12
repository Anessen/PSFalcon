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
## Managing User Groups
### List User groups by ID
```powershell
Get-FalconUserGroup [-Detailed] [-All]
```
### Retrieve detail about one or more User groups
```powershell
Get-FalconUserGroup -Ids <id>, <id>
```
### Create a User group
```powershell
New-FalconUserGroup -Name 'Manual Testing' -Description 'Manual Testing'
```
### Update a User group
```powershell
Edit-FalconUserGroup -Id <id> -Name 'Updated Name' -Description 'Updated name for manual testing'
```
### Delete a User group
```powershell
Remove-FalconUserGroup -Ids <id>, <id>
```
## Managing CID group members
## Managing User group members
## Managing role assignments
### Get role assignments
```powershell
```
### Create a role assignment
```powershell
```
### Delete a role assignment
```powershell
```
_See CrowdStrike API Documentation[]()._