![CrowdStrike Falcon](https://raw.githubusercontent.com/CrowdStrike/falconpy/main/docs/asset/cs-logo.png)

|Command|Permission|
|-------|----------|
|[Register-FalconEventCollector](https://github.com/CrowdStrike/psfalcon/wiki/Third-party-ingestion#configure-a-humio-collector)| |
|[Send-FalconEvent](https://github.com/CrowdStrike/psfalcon/wiki/Third-party-ingestion#send-objects-to-humio)| |
|[Send-FalconWebhook](https://github.com/CrowdStrike/psfalcon/wiki/Third-party-ingestion#webhook-ingestion)| |
|[Show-FalconEventCollector](https://github.com/CrowdStrike/psfalcon/wiki/Third-party-ingestion#display-your-collector)| |
|[Unregister-FalconEventCollector](https://github.com/CrowdStrike/psfalcon/wiki/Third-party-ingestion#remove-your-collector)| |

# Humio event ingestion
## Configure a Humio collector
The `-Enable` parameter is optional and will configure PSFalcon to send `requests` or `responses` to Humio as they occur.
```powershell
Register-FalconEventCollector -Uri https://cloud.community.humio.com -Token <string> -Enable responses, requests
```
The `-Token` parameter expects your [Humio ingest token](https://library.humio.com/stable/docs/ingesting-data/ingest-tokens/).
## Display your collector
```powershell
Show-FalconEventCollector
```
## Remove your collector
```powershell
Unregister-FalconEventCollector
```
## Send objects to Humio
Once a collector has been defined through `Register-FalconEventCollector`, any `[PSCustomObject]` can be sent to Humio.
```powershell
Get-FalconHost -Limit 1 -Detailed | Send-FalconEvent
```
```powershell
Send-FalconEvent -Object ([PSCustomObject]@{ Example = 'my_string' })
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