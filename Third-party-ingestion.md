![CrowdStrike Falcon](https://raw.githubusercontent.com/CrowdStrike/falconpy/main/docs/asset/cs-logo.png)
***
- [Falcon LogScale event ingestion](#falcon-logscale-event-ingestion)
    - [Configure a Falcon Logscale collector](#configure-a-falcon-logscale-collector)
    - [Display your collector](#display-your-collector)
    - [Send objects to Falcon Logscale](#send-objects-to-falcon-logscale)
    - [Remove your collector](#remove-your-collector)
- [Webhook ingestion](#webhook-ingestion)
    - [Send objects to Slack](#send-objects-to-slack)
- [Falcon Intelligence indicator map](#falcon-intelligence-indicator-map)
    - [Map indicators](#map-indicators)
***
|Command|Permission|
|-------|----------|
|[Register-FalconEventCollector](#configure-a-falcon-logscale-collector)||
|[Send-FalconEvent](#send-objects-to-falcon-logscale)||
|[Send-FalconWebhook](#send-objects-to-slack)||
|[Show-FalconEventCollector](#display-your-collector)||
|[Show-FalconMap](#map-indicators)||
|[Unregister-FalconEventCollector](#remove-your-collector)||
***
# Falcon LogScale event ingestion
## Configure a Falcon LogScale collector
The `Enable` parameter is optional and will configure PSFalcon to send `requests` or `responses` to Falcon
LogScale as they occur.

The `Token` parameter expects your Falcon LogScale [ingest token](https://library.humio.com/stable/docs/ingesting-data/ingest-tokens/).
```powershell
Register-FalconEventCollector -Uri https://cloud.community.humio.com -Token <string> -Enable responses, requests
```
## Display your collector
```powershell
Show-FalconEventCollector
```
## Send objects to Falcon LogScale
Once a collector has been defined through `Register-FalconEventCollector`, any `[PSCustomObject]` can be sent to
Falcon LogScale.
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
$Object = [PSCustomObject]@{ Example = 'my_string' }
Send-FalconWebhook -Type Slack -Uri https://hooks.slack.com/services/... -Object $Object
```
# Falcon Intelligence indicator map
## Map indicators
```powershell
Get-FalconIndicator -Filter "type:'hash_sha256'" -Limit 5 | Show-FalconMap
```
```powershell
Show-FalconMap -Indicator www.google.com, 8.8.8.8
```