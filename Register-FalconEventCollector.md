# Register-FalconEventCollector
## SYNOPSIS
Define Falcon LogScale ingestion endpoint and token for logging
## DESCRIPTION
Once configured, the Falcon LogScale destination can be used by PSFalcon but the module will not send events to
Falcon LogScale until 'Enable' options are chosen. 'Remove-FalconEventCollector' can be used to remove a
configured destination and stop the transmission of events.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Uri|Uri|Falcon LogScale cloud|||||X|
|Token|String|Falcon LogScale ingestion token|||||X|
|Enable|String[]|Define events to send to the collector|||`responses`<BR>`requests`||X|
## SYNTAX
```powershell
Register-FalconEventCollector [-Uri] <Uri> [-Token] <String> [[-Enable] <String[]>] [<CommonParameters>]
```
## USAGE
### Configure a Falcon LogScale collector
The `Enable` parameter is optional and will configure PSFalcon to send `requests` or `responses` to Falcon
LogScale as they occur.

The `Token` parameter expects your Falcon LogScale [ingest token](https://library.humio.com/stable/docs/ingesting-data/ingest-tokens/).
```powershell
Register-FalconEventCollector -Uri https://cloud.community.humio.com -Token <string> -Enable responses, requests
```
### Set a Falcon LogScale collector during your authorization request
```powershell
Request-FalconToken -ClientId <string> -ClientSecret <string> -Collector @{ uri = 'string'; token = 'string' }
```

_2023-11-27: PSFalcon v2.2.6_
