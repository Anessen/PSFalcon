![CrowdStrike Falcon](https://raw.githubusercontent.com/CrowdStrike/falconpy/main/docs/asset/cs-logo.png)

|Command|Permission|
|-------|----------|
|[Register-FalconEventCollector](Third-party-ingestion#configure-a-falcon-logscale-collector)| |
|[Send-FalconEvent](Third-party-ingestion#send-objects-to-falcon-logscale)| |
|[Send-FalconWebhook](Third-party-ingestion#webhook-ingestion)| |
|[Show-FalconEventCollector](Third-party-ingestion#display-your-collector)| |
|[Show-FalconMap](Third-party-ingestion#map-indicators)| |
|[Unregister-FalconEventCollector](Third-party-ingestion#remove-your-collector)| |

# Falcon LogScale event ingestion
## Configure a Falcon LogScale collector
The `-Enable` parameter is optional and will configure PSFalcon to send `requests` or `responses` to Falcon LogScale as they occur.

The `-Token` parameter expects your [Humio ingest token](https://library.humio.com/stable/docs/ingesting-data/ingest-tokens/).
```powershell
Register-FalconEventCollector -Uri https://cloud.community.humio.com -Token <string> -Enable responses, requests
```
## Display your collector
```powershell
Show-FalconEventCollector
```
## Send objects to Falcon LogScale
Once a collector has been defined through `Register-FalconEventCollector`, any `[PSCustomObject]` can be sent to Falcon LogScale.
```powershell
Get-FalconHost -Limit 1 -Detailed | Send-FalconEvent
```
```powershell
Send-FalconEvent -Object ([PSCustomObject]@{ Example = 'my_string' })
```
## Remove your collector
```powershell
Unregister-FalconEventCollector
```
# Webhook ingestion
## Send objects to Slack
Any `[PSCustomObject]` can be sent to a Slack webhook.
```powershell
Get-FalconHost -Limit 1 -Detailed | Send-FalconWebhook -Type Slack -Uri https://hooks.slack.com/services/... 
```
```powershell
Send-FalconWebhook -Type Slack -Uri https://hooks.slack.com/services/... -Object ([PSCustomObject]@{ Example = 'my_string' })
```
# Falcon Intelligence Indicator Map
## Map indicators
```powershell
Get-FalconIndicator -Filter "type:'hash_sha256'" -Limit 5 | Show-FalconMap
```
```powershell
Show-FalconMap -Indicator www.google.com, 8.8.8.8
```