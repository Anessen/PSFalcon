## View installation token settings
```powershell
Get-FalconInstallTokenSettings
```
## Create installation tokens
```powershell
New-FalconInstallToken -Label "My Token" -ExpiresTimestamp "2021-12-31T00:00:00Z"
```
## Find installation tokens
```powershell
Get-FalconInstallToken [-Detailed] [-All]
```
### Get information about an installation token
```powershell
Get-FalconInstallToken -Ids <id>, <id>
```
## Modify an installation token
```powershell
Edit-FalconInstallToken -Ids <id>, <id> -Revoked $true
```
```powershell
Edit-FalconInstallToken -Ids <id> -Label "Token no expiration" -ExpiresTimestamp null
```
## Delete installation tokens
```powershell
Remove-FalconInstallToken -Ids <id>, <id>
```
## View installation token audit events

```powershell
Get-FalconInstallTokenEvent [-Detailed] [-All]
```
### Get information about an installation token audit event
```powershell
Get-FalconInstallTokenEvent -Ids <id>, <id>
```
_See [CrowdStrike API Documentation](https://falcon.crowdstrike.com/support/documentation/120/Installation-token-APIs)._