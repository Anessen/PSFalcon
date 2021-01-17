### Create a new user

```powershell
New-FalconUser -Username jane.doe@example.com
```

### List all users

```powershell
Get-FalconUser [-Detailed]
```

### Get details on one or more users

```powershell
Get-FalconUser -Ids <id>, <id>
```

### Modify a user

```powershell
Edit-FalconUser -Id <id> -FirstName Jane -LastName Doe
```

### Remove a user

```powershell
Remove-FalconUser -Id <id>
```

### List all available user roles

```powershell
Get-FalconRole [-Detailed]
```

### List roles assigned to a user

```powershell
Get-FalconRole -UserId <id> [-Detailed]
```

### Assign roles to a user

```powershell
Add-FalconRole -Ids <id>, <id> -UserId <id>
```

### Revoke roles from a user

```powershell
Remove-FalconRole -Ids <id>, <id> -UserId <id>
```

[CrowdStrike API Documentation](https://falcon.crowdstrike.com/support/documentation/87/users-and-roles-apis)