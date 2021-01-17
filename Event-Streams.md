### Start an event stream

```powershell
Get-FalconStream -AppId psfalcon
```

### Refresh an active event stream

```powershell
Update-FalconStream -ActionName refresh_active_stream_session -AppId psfalcon -Partition 0
```

[CrowdStrike API Documentation](https://falcon.crowdstrike.com/support/documentation/89/event-streams-apis)