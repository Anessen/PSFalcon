# Invoke-FalconIdentityGraph
## SYNOPSIS
Interact with Falcon Identity using GraphQL
## DESCRIPTION
The 'All' parameter requires that your GraphQL statement contain an 'after' cursor variable definition and
'pageInfo { hasNextPage endCursor }'.

Requires 'Identity Protection GraphQL: Write', and other 'Identity Protection' permission(s) depending on query.
## PARAMETERS
|Name|Type|Description|Min|Max|Allowed|Pipeline|PipelineByName|
|----|----|-----------|---|---|-------|--------|--------------|
|String|String|A complete GraphQL statement||||X||
|Variable|Hashtable|A hashtable containing variables used in your GraphQL statement||||X||
|All|Switch|Repeat requests until all available results are retrieved||||||
## SYNTAX
```powershell
Invoke-FalconIdentityGraph [-String] <String> [[-Variable] <Hashtable>] [-All] [-WhatIf] [-Confirm] [<CommonParameters>]
```
## USAGE
Queries can be created using *GraphiQl*. \[ [US-1](https://falcon.crowdstrike.com/id-protection/ui-api/graphql) | [US-2](https://falcon.us-2.crowdstrike.com/id-protection/ui-api/graphql) | [EU-1](https://falcon.eu-1.crowdstrike.com/id-protection/ui-api/graphql) | [US-GOV-1](https://falcon.laggar.gcw.crowdstrike.com/id-protection/ui-api/graphql) \]
```powershell
$Query = '{
  entities(types: [USER], archived: false, first: 10, dataSources: [ACTIVE_DIRECTORY]) {
    nodes {
      primaryDisplayName
      secondaryDisplayName
      riskScoreSeverity
      accounts {
        description
        ... on ActiveDirectoryAccountDescriptor {
          passwordAttributes {
            lastChange
          }
          creationTime
          objectSid
          samAccountName
          domain
          enabled
          ou
          lastUpdateTime
        }
      }
    }
  }
}'
Invoke-FalconIdentityGraph -String $Query
```
To have the results paginated using the `All` parameter, you must define a `Cursor` variable, and include it within
`entities` along with the relevant `pageInfo` properties. When the results are paginated using `All`, PSFalcon will
display the contents of `entities.nodes` directly, rather than the entire response object (similar to other
PSFalcon commands).
```powershell
$Query = 'query ($after: Cursor) {
  entities(types: [USER], archived: false, after: $after, first: 10, dataSources: [ACTIVE_DIRECTORY]) {
    nodes {
      primaryDisplayName
      secondaryDisplayName
      riskScoreSeverity
      accounts {
        description
        ... on ActiveDirectoryAccountDescriptor {
          passwordAttributes {
            lastChange
          }
          creationTime
          objectSid
          samAccountName
          domain
          enabled
          ou
          lastUpdateTime
        }
      }
    }
    pageInfo {
      hasNextPage
      endCursor
    }
  }
}'
Invoke-FalconIdentityGraph -String $Query -All
```
### Query for the first 5 administrator accounts
```powershell
Invoke-FalconIdentityGraph -String '{entities(roles:[BuiltinAdministratorRole] sortKey:PRIMARY_DISPLAY_NAME sortOrder:ASCENDING first:5) {nodes{primaryDisplayName secondaryDisplayName}}}'
```
### Query for the top 10 users with the highest risk score
```powershell
Invoke-FalconIdentityGraph -String '{entities(types:[USER] minRiskScoreSeverity:MEDIUM sortKey: RISK_SCORE sortOrder:DESCENDING first:10) {nodes{primaryDisplayName secondaryDisplayName isHuman:hasRole(type:HumanUserAccountRole) isProgrammatic:hasRole(type:ProgrammaticUserAccountRole) ... on UserEntity{emailAddresses} riskScore riskScoreSeverity riskFactors {type severity}}}}'
```
### Query for accounts that have not completed learning mode
```powershell
$Query = 'query ($after: Cursor) {
  entities(types: [USER], archived: false, learned: false, after: $after, first: 1000) {
    nodes {
      primaryDisplayName
      secondaryDisplayName
      accounts {
        ... on ActiveDirectoryAccountDescriptor {
          domain
        }
      }
    }
    pageInfo {
      hasNextPage
      endCursor
    }
  }
}'
Invoke-FalconIdentityGraph -String $Query -All
```

_2023-04-25: PSFalcon v2.2.5_
