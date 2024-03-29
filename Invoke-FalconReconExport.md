# Invoke-FalconReconExport
## SYNOPSIS
Initiate a Falcon Intelligence Recon export job
## DESCRIPTION
Requires 'Monitoring rules (Falcon Intelligence Recon): Write'.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|Entity|String|Entity type|||`notification-exposed-data-record`|||
|Filter|String|[Falcon Query Language](Filtering-Results) expression to limit results||||||
|Sort|String|Property and direction to sort results|||`author\|asc`<BR>`author\|desc`<BR>`author_id\|asc`<BR>`author_id\|desc`<BR>`cid\|asc`<BR>`cid\|desc`<BR>`created_date\|asc`<BR>`created_date\|desc`<BR>`credentials_domain\|asc`<BR>`credentials_domain\|desc`<BR>`credentials_ip\|asc`<BR>`credentials_ip\|desc`<BR>`display_name\|asc`<BR>`display_name\|desc`<BR>`domain\|asc`<BR>`domain\|desc`<BR>`email\|asc`<BR>`email\|desc`<BR>`email_domain\|asc`<BR>`email_domain\|desc`<BR>`exposure_date\|asc`<BR>`exposure_date\|desc`<BR>`file.complete_data_set\|asc`<BR>`file.complete_data_set\|desc`<BR>`financial.bank_account\|asc`<BR>`financial.bank_account\|desc`<BR>`financial.credit_card\|asc`<BR>`financial.credit_card\|desc`<BR>`financial.crypto_currency_addresses\|asc`<BR>`financial.crypto_currency_addresses\|desc`<BR>`hash_type\|asc`<BR>`hash_type\|desc`<BR>`id\|asc`<BR>`id\|desc`<BR>`impacted_domain\|asc`<BR>`impacted_domain\|desc`<BR>`impacted_ip\|asc`<BR>`impacted_ip\|desc`<BR>`location.country_code\|asc`<BR>`location.country_code\|desc`<BR>`location.postal_code\|asc`<BR>`location.postal_code\|desc`<BR>`login_id\|asc`<BR>`login_id\|desc`<BR>`notification_id\|asc`<BR>`notification_id\|desc`<BR>`phone_number\|asc`<BR>`phone_number\|desc`<BR>`rule.id\|asc`<BR>`rule.id\|desc`<BR>`rule.topic\|asc`<BR>`rule.topic\|desc`<BR>`site\|asc`<BR>`site\|desc`<BR>`site_id\|asc`<BR>`site_id\|desc`<BR>`social.aim_id\|asc`<BR>`social.aim_id\|desc`<BR>`social.facebook_id\|asc`<BR>`social.facebook_id\|desc`<BR>`social.icq_id\|asc`<BR>`social.icq_id\|desc`<BR>`social.instagram_id\|asc`<BR>`social.instagram_id\|desc`<BR>`social.msn_id\|asc`<BR>`social.msn_id\|desc`<BR>`social.skype_id\|asc`<BR>`social.skype_id\|desc`<BR>`social.twitter_id\|asc`<BR>`social.twitter_id\|desc`<BR>`social.vk_id\|asc`<BR>`social.vk_id\|desc`<BR>`social.vk_token\|asc`<BR>`social.vk_token\|desc`<BR>`source_category\|asc`<BR>`source_category\|desc`<BR>`user_id\|asc`<BR>`user_id\|desc`<BR>`user_ip\|asc`<BR>`user_ip\|desc`<BR>`user_name\|asc`<BR>`user_name\|desc`<BR>`user_uuid\|asc`<BR>`user_uuid\|desc`|||
|ExportType|String|Export file format|||`csv`<BR>`json`|||
|HumanReadable|Boolean|Use property names that match the Falcon UI||||||
## SYNTAX
```powershell
Invoke-FalconReconExport [-Entity] <String> [-Filter] <String> [-Sort] <String> [-ExportType] <String> [-HumanReadable] <Boolean> [-WhatIf] [-Confirm] [<CommonParameters>]
```
## REFERENCE
### Endpoints
```
POST /recon/entities/exports/v1
```
### falconpy
[CreateExportJobsV1](https://github.com/CrowdStrike/falconpy/wiki/recon#CreateExportJobsV1)
## USAGE

_2023-04-25: PSFalcon v2.2.5_
