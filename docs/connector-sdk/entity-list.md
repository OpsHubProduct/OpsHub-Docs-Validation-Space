## Overview
Return the list of entities matching the search criteria.

## API URI
This is the URI, OpsHub will execute to call this API:
```bash
POST: /entities/{entityTypeId}/search? 
projectId=<projectId>
&startIndex=<startIndex>
&maxResults=<maxResults>
&nextPageLink=<nextPageLink>
```

## URI Parameters

| Name          | In    | Required | Type     | Description |
|---------------|-------|----------|----------|-------------|
| entityTypeId  | path  | True     | String   | ‘id’ of entity type for which the list of entities needs to be returned |
| projectId     | query | False    | String   | ‘id’ of the project for which the list of entities needs to be returned |
| startIndex    | query | True     | Integer  | Start index from which matching entities need to be returned |
| maxResults    | query | True     | Integer  | Number of entities from startIndex that need to be returned |
| nextPageLink  | query | False    | URL      | Link to the next page of entity list response.<br><br>If the connector returns the next page link in the response, in the subsequent paginated requests, OIM will pass that next page link.<br><br>`startIndex` and `pageSize` will still be passed along with `nextPageLink`.<br><br>Connector can utilize this parameter so that for subsequent pages, connector doesn't need to form the end system query again. |

---

## Request Body
It contains search criteria which is required to be applied in the end system to fetch the matching entities.

- OpsHub has developed its own query format to query any end system.
- Refer to **[OpsHub Query Format Guide](../integrate/opshub-query-format.md)** for a detailed understanding of the OpsHub queries.
- {{SITENAME}} will pass the query object as JSON payload which Connector SDK will parse and convert to end system’s native query.
- Most queries done by OpsHub contain complex queries with the following fields:
  - project
  - entity id
  - created Date
  - updated Date
  - created By

---

## Request Payload
*Request Payload can be constructed using following details:*

```
field name:

  field internal name being used in end system's native query. If ‘isCriteriaInSystemNativeFormat’ in entity-types/<entity-type-id> API is true, then for criteria query specified by user in OpsHub integration configuration, query will be passed as it is with field name =’OH_NATIVE_QUERY’

operator:

 for single valued query:

EQUALS, GREATER_THAN, GREATER_THAN_EQUALS, LESS_THAN, LESS_THAN_EQUALS, NOT_EQUALS

for multi valued query:

IN

for complex query:

AND, NOT

value:

 single value which will be added to the query. If ‘isCriteriaInSystemNativeFormat’ in entity-types/<entity-type-id> API is true, then for criteria query specified by user in OpsHub integration configuration, query will be passed as given by user in ‘value’.

values:

 multiple values which will be added to the query.

criteria:

can be any of the following:

single valued query

{
  "field": "<field name>",
  "condition": "<operator>",
  "value": "<value>"
}

multi valued query

{
  "field": "<field name>",
  "condition": "<operator>",
  "values": [<value1>,<value2>]
}

complex query

{
  "condition": "<operator>",
  "criterias": [<criteria1>,<criteria2>]
}
```

**Example 1:** Entities created by integration user after a given time:  

```json
{
  "query": {
    "condition": "and",
    "criterias": [
      {
        "field": "<createdByField>",
        "condition": "=",
        "value": "integration.user"
      },
      {
        "field": "<createdDateField>",
        "condition": ">",
        "value": "2021-02-15T08:00:00Z"
      }
    ]
  },
  "orderBy": [
    {
      "fieldName": "<createdDateField>",
      "direction": "ASC"
    },
    {
      "fieldName": "<entityIdField>",
      "direction": "ASC"
    }
  ]
}
```
Example 2: Entities updated after a given time and meets native criteria specified by end user in OpsHub. In the following sample request, the API must return entities updated after 2021-02-15T08:00:00Z and whose State = ‘Resolved’ and Team = ‘Marvels’.

```json
{
  "query": {
    "condition": "and",
    "criterias": [
      {
        "field": "<updatedDateField>",
        "condition": ">",
        "value": "2021-02-15T08:00:00Z"
      },
      {
        "field": "OH_NATIVE_QUERY",
        "condition": "=",
        "value": "State = ‘Resolved’ and Team = ‘Marvels’"
      }
    ]
  },
  "orderBy": [
    {
      "fieldName": " updatedDateField ",
      "direction": "DESC"
    }
  ]
}
```

Following are some search criteria that OpsHub will call **Entity – List API** for:

- **Polling query**  
  - `updatedDate >= pollingTime` and `updatedDate <= maxTime`
- **Entities created after given time by integration user**  
  - `CreatedDate > time` and `createdBy = integrationUser`
- **Is entity updated after given time?**  
  - `UpdatedDate > time` and `entityId = <entityId>`
- **Criteria**  
  - `UpdatedDate >= pollingTime` and `<user condition>`  
  - `<user condition>` can be JSON or in native end system format, in which case conversion is not required.
- **Getting max time**  
  - `UpdatedDate >= pollingTime`
- **Target lookup**  
  - `<user condition>`, typically: `entityId = <entityId>`  
  - Sometimes: `entityId = <entityId>` and `customField = <someId>`

---

## Response Payload

The list of entities matching the selection criteria sent as part of the request payload should be returned.

> **Note:**  
> Fields provided in [fieldNameInfo in response payload for Entity Type-Get API](entity-type-get.md#response-payload) and any field which can be configured for end system criteria storage should be part of the response payload.  
> For more details regarding end system criteria storage, refer to [Criteria Configuration](../integrate/integration-configuration.md#criteria-configuration).

```json
{
  "nextPageLink": "// Link to the next page if returned by the end system",
  "nextPageLinkSupported": "true/false | datatype: boolean",
  "entities": [
    {
      "fields": {
        "<field1>": "field1_value",
        "<field2>": [
          "<field2_Value1>",
          "<field2_value2>"
        ],
        "<field3>": true,
        "<field4>": 1000,
        "<userField>": "userName",
        "<entityIdField>": "1",
        "<entityDisplayIdField>": "",
        "<entityTypeIdField>": "",
        "<projectIdField>": "// required if project-based structure",
        "<createdDateField>": "// required if entity-type is time-based",
        "<updatedDateField>": "// required if entity-type is time-based",
        "<createdByField>": "// required if entity-type is time-based",
        "<updatedByField>": "// required if entity-type is time-based"
      }
    }
  ]
}
```


