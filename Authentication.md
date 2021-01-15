## Requesting an Authentication Token
During a PowerShell session, you must have a valid OAuth2 token in order to make requests to the CrowdStrike Falcon API endpoints.

If you have already input your credentials, PSFalcon requests a token on your behalf when you issue a command. Otherwise, you must request a token and provide the credentials. You can do this using `Request-FalconToken`, or input your Id/Secret when prompted after issuing a PSFalcon command.

```powershell
Request-FalconToken
ClientId: <string>
ClientSecret: <string>
```

After a valid OAuth2 token is received, it caches with your credentials. Your cached token is checked and refreshed as needed while running PSFalcon commands.

### Revoking an Authentication Token

Authentication tokens expire after 30 minutes. If you wish to revoke an existing token, you can use `Revoke-FalconToken`.

**NOTE**: Revoking a token will also clear your credentials. This is useful if you wish to switch between different Falcon environments.

```powershell
Revoke-FalconToken
```

## Child environments
If you're using an MSSP configuration, you can target specific child environments using the `-CID` parameter during authentication token requests. Your choice is saved and all requests are sent to that particular CID unless a new `Request-FalconToken` request is made specifying a new child environment.

## Alternate clouds
Authentication token requests are sent to the “us-1“ cloud by default. You may use the `-Cloud` parameter to choose a different cloud destination.

The accepted hostname values can be viewed using tab auto-completion after entering the `-Cloud` parameter, or through `Request-FalconToken -Help`. Your cloud choice is saved and all requests are sent to the chosen cloud unless a new `Request-FalconToken` request is made specifying a new cloud.