## Requesting a Token
During a PowerShell session, you must have a valid OAuth2 access token in order to make requests to the CrowdStrike Falcon APIs.

If you have already provided your credentials, PSFalcon requests a token on your behalf when you issue a command. Otherwise, you must request a token and provide the credentials. You can do this using `Request-FalconToken`, or input your ClientId/ClientSecret when prompted after issuing a PSFalcon command.

**NOTE**: If you allow the module to prompt for your ClientId/ClientSecret, you will default to the 'us-1' Cloud.
```powershell
Request-FalconToken
ClientId: <string>
ClientSecret: <string>
```
After a valid OAuth2 token is received, it is cached with your credentials. Your cached token is checked and refreshed as needed while running PSFalcon commands.

### Child environments
If you're using an MSSP ("Flight Control") configuration, you can target specific child environments using the `-MemberCid` parameter during authentication token requests. Your choice is saved and all requests are sent to that particular member CID unless a new `Request-FalconToken` request is made specifying a new member CID.

### Alternate clouds
Authentication token requests are sent to the `us-1` cloud by default. You may use the `-Cloud` parameter to choose a different Cloud environment, or `-Hostname` to set it using the full URL value.

The accepted hostname values can be viewed using tab auto-completion after entering the `-Cloud` or `-Hostname` parameter(s). Your Cloud/Hostname choice is saved and all requests are sent using the cached information.

## Revoking a Token
Authentication tokens expire after 30 minutes. If you wish to revoke an existing token, you can use `Revoke-FalconToken`.

**NOTE**: Revoking a token will also clear your credentials. This is useful if you wish to switch between different Falcon environments.
```powershell
Revoke-FalconToken
```

## Verifying token status
`Test-FalconToken` can be used to verify whether you have an active OAuth2 access token cached. The `Token` property of the output from `Test-FalconToken` provides a `[boolean]` value of your current status.
```powershell
(Test-FalconToken).Token
```
_Learn more about [Commands](https://github.com/CrowdStrike/psfalcon/wiki/Commands)._