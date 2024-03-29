# Send-FalconWebhook
## SYNOPSIS
Send a PSFalcon object to a supported Webhook
## DESCRIPTION
Sends an object to a Webhook, converting the object to an acceptable format when required
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Type|String|Webhook type|||`Slack`|||
|Path|Uri|Webhook URL||||||
|Label|String|Message label||||||
|Object|Object|Response object to format||||X||
## SYNTAX
```powershell
Send-FalconWebhook [-Type] <String> [-Path] <Uri> [[-Label] <String>] [-Object] <Object> [<CommonParameters>]
```
## USAGE
### Send objects to Slack
Any `[PSCustomObject]` can be sent to a Slack webhook.
```powershell
Get-FalconHost -Limit 1 -Detailed | Send-FalconWebhook -Type Slack -Uri https://hooks.slack.com/services/... 
```
```powershell
$Object = [PSCustomObject]@{ Example = 'my_string' }
Send-FalconWebhook -Type Slack -Uri https://hooks.slack.com/services/... -Object $Object
```

_2023-04-25: PSFalcon v2.2.5_
