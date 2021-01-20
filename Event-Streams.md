### Start an event stream

```powershell
Get-FalconStream -AppId psfalcon
```

### Refresh an active event stream

```powershell
Update-FalconStream -ActionName refresh_active_stream_session -AppId psfalcon -Partition 0
```

### Capture a sample of events from a stream

```powershell
Open-FalconStream
```
**NOTE**: This is a custom command included with PSFalcon. Over a few minutes, `Open-FalconStream` will output an event stream to a Json file in the local directory. It currently only works on Windows and will open a secondary session when executed. You can close the session to write the Json to disk.

_See [CrowdStrike API Documentation](https://falcon.crowdstrike.com/support/documentation/89/event-streams-apis)._