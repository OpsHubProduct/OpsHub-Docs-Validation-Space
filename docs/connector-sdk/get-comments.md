## Overview
Return existing comments for the given entity ID.

## API URI
```bash
GET: /entities/{entityTypeId}/{entityId}/comments?projectId={projectId}&startIndex=<startIndex>&maxResults=<maxResults>&nextPageLink=<nextPageLink>&afterTime=<afterTime>
```


## URI Parameters
| **Name**        | **In** | **Required** | **Type**  | **Description** |
|-----------------|--------|--------------|-----------|-----------------|
| entityTypeId    | path   | True         | String    | `id` of entity type for given entityId |
| entityId        | path   | True         | String    | `id` of entity for which comments need to be returned |
| projectId       | query  | True         | String    | Project in which the given entity exists |
| startIndex      | query  | True         | Integer   | Start index from which comments need to be returned |
| maxResults      | query  | True         | Integer   | Number of comments from `startIndex` that need to be returned |
| nextPageLink    | query  | False        | String    | Link to the next page if returned by the end system |
| afterTime       | query  | False        | String    | Time after which the comments are to be filtered.<br><br>The `afterTime` date format will be the same as provided in [`comments.createUpdateDateFormat` in response payload for Entity Type – Get API](entity-type-get.md#response-payload), and `timeZone` will be the same as provided in [`timeZone` in response payload for Server-Info API](server-info.md#response-payload).<br><br>- If the end system API does not support time-based filtering on comments, this parameter may be ignored.<br>- If the end system API supports time-based filtering on comments, the connector should return the comments with a createdUpdatedTime greater than the specified afterTime.<br>- If “null” is passed in the “afterTime” then connector needs to return all the comments without any time filter applied.

## Response Payload
```json
{
  "nextPageLink": "// Link to the next page if returned by the end system",
  "nextPageLinkSupported": "true/false | datatype: boolean",
  "comments": [
    {
      "<idField>": "",
      "<titleField>": "",
      "<bodyField>": "",
      "<createdByField>": "",
      "<createdDateField>": "",
      "<updatedByField>": "",
      "<updatedDateField>": "",
      "<commentTypeField>": ""
    }
  ]
}
```


>**Note**": The key names in the above JSON will be as per the comment field names in your connector.



