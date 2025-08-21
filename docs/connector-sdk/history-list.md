# History – List API

## Overview
Returns history for the given entity type, filtered by project, entity id, time or user and sorted (if supported by end system) according to the given `orderByDirection`.

## API URI
```
GET: /entities/{entityTypeId}/history? 
     projectId=<projectId> 
     &entityId=<entityId> 
     &since=<sinceTime> 
     &maxTime=<maxTime> 
     &notUpdatedByUser=<notUpdatedByUser> 
     &startIndex=<startIndex> 
     &maxResults=<maxResults>
     &nextPageLink=<nextPageLink>
     &orderByDirection=<orderByDirection>
```

## URI Parameters
| Name              | In     | Required | Type     | Description |
|-------------------|--------|----------|----------|-------------|
| entityTypeId      | path   | True     | String   | ‘id’ of the entity type for the given entity id |
| entityId          | path   | False    | String   | ‘id’ of the entity for which history needs to be returned |
| projectId         | Query  | True     | String   | Project for which history needs to be returned |
| since             | Query  | False    | Datetime | Returns history that has occurred since this time (`history >= sinceTime`) |
| maxTime           | Query  | False    | Datetime | Returns history that occurred before or on this time (`history <= maxTime`) |
| notUpdatedByUser  | Query  | False    | String   | Returns history for updates that the given user did not do. The user’s username or email will be passed as per the `IntegrationUserDatatype` parameter in ServerInfo API |
| startIndex        | Query  | True     | Integer  | Starts index from where history items need to be returned |
| maxResults        | Query  | True     | Integer  | The number of history items from `startIndex` that needs to be returned |
| nextPageLink      | Query  | False    | String   | Link to the next page of the history list response. If connector returns the next page link in a response, in the subsequent paginated requests, OIM will pass that `nextPageLink`. `startIndex` and `pageSize` will still be passed along with `nextPageLink`. Connector can utilize this parameter so that for subsequent pages, it doesn't need to form the end system query again. |
| orderByDirection  | Query  | False    | String   | Sorts the history based on `orderByDirection`. Values: `ASC` or `DESC`. Sorting priority: 1. `CREATE_UPDATED_TIME` 2. `ENTITY_ID` 3. `REVISION_ID`. If not supported, set `sortableFields` as `null`. |

## Response Payload
```
{
  "nextPageLink": "// Link to the next page if returned by the end system",
  "nextPageLinkSupported": "true/false | datatype: boolean",
  "revisions": [
    {
      "entityId": "<unique id of entity>",
      "revisionId": "<revision number>",
      "updatedBy": "<username of user who made the change>",
      "revisionDateTime": "<revision time>",
      "revisionType": "CREATE / UPDATE",
      "fieldsChangedInRevision": {
        "<field1_string_field>": {
          "oldValue": "value 1",
          "newValue": "value 2"
        },
        "<field2_boolean_field>": {
          "oldValue": false,
          "newValue": true
        },
        "<field3_multi_select_field>": {
          "oldValue": [1, 2, 3],
          "newValue": [2, 4, 6]
        }
      },
      "attachmentRevision": {
        "oldValue": [
          {
            "<idField>": "",
            "<contentUriField>": "",
            "<fileNameField>": "",
            "<contentTypeField>": "",
            "<contentLengthField>": ""
          }
        ],
        "newValue": [
          {
            "<idField>": "",
            "<contentUriField>": "",
            "<fileNameField>": "",
            "<contentTypeField>": "",
            "<contentLengthField>": ""
          }
        ]
      },
      "commentRevision": {
        "newValue": {
          "<idField>": "",
          "<titleField>": "",
          "<bodyField>": "",
          "<commentTypeField>": ""
        }
      },
      "linkRevision": {
        "oldValue": [
          {
            "<idField>": "",
            "<linkTypeField>": "",
            "<linkedEntityIdField>": "",
            "<linkedEntityTypeField>": "",
            "<linkedEntityScopeIdFieldName>": ""
          }
        ],
        "newValue": [
          {
            "<idField>": "",
            "<linkTypeField>": "",
            "<linkedEntityIdField>": "",
            "<linkedEntityTypeField>": "",
            "<linkedEntityScopeIdFieldName>": ""
          }
        ]
      }
    }
  ]
}
```
## Response Body

| Parent              | Name                   | Type     | Description |
|---------------------|------------------------|----------|-------------|
| revisions           |                        |          | Revisions should be sorted on `revisionDateTime`, `entityId`, and `revisionId` in ascending order. First compare `revisionDateTime`; if equal, compare `entityId`; if still equal, compare `revisionId`. |
|                     | entityId               | String   | 'id' of the entity for which the history record is returned. |
|                     | revisionId             | String   | Unique id to identify a revision if the end system does not maintain the revision id. |
|                     | updatedBy              | String   | Username of the user who created the given history record. |
|                     | revisionDateTime       | Datetime | Time at which the update was performed.<br><br>**Note:** When end system API does not provide information for revision of either of comments/attachments/links in the history API, provide dummy revision for these with providing the revisionDateTime when comment(s)/attachment(s)/link(s) has been created or updated for the entity whose history is returned. For example, An entity E1's field F1 is updated at timestamp T1, and a comment C1 is added to E1 at timestamp T2 (T2 > T1), and history API only provides revision for field F1, then end system needs to provide dummy revision for the comment C1 as follows:<br>  ```json { "entityId": "<unique id of entity>", "revisionId": "<revision number>", "updatedBy": "<username of user who made the change>",  "revisionDateTime": "<revision time>",  "revisionType": "CREATE / UPDATE"} ``` |
|                     | revisionType           | Enum     | Type of revision: `CREATE` or `UPDATE`.<br><br>- **CREATE:** Send when the entity was created in this revision. This can be determined using system-specific rules (e.g., `revisionId` = 0 or matching entity creation time). If determination is not possible, send `UPDATE` instead.<br>- **UPDATE:** Entity was updated in this revision. |
|                     | fieldsChangedInRevision| Object   | Fields modified in this revision. If none were modified, can be empty. For each field, send `oldValue` (value before this revision) and `newValue` (value set in this revision). Multi-select fields should send full lists for both old and new values.<br><br>**For CREATE Revision:** Pass `null`.<br><br>If parsing old/new field values is complex, the full history description can be placed in the field name `OH_HISTORY_DESCRIPTION` with `newValue` containing the description.<br><br>**Example:**<br>```json\n\"OH_HISTORY_DESCRIPTION\": {\n  \"oldValue\": null,\n  \"newValue\": \"<history_description_string>\"\n}\n``` |
|                     | attachmentRevision     | Object   | Returns the list of attachments that existed in the entity in the previous revision, in oldValue. <br> In newValue, send a list of attachments that exists as of this revision. If no attachment was added, deleted or modified in this revision OR the end system has a separate API for fetching attachment history, then attachmentRevision can be null |
|                     | commentRevision        | Object   | In newValue, send any comment newly added or modified in this revision. <br>If no comment was added or modified in this revision OR the end system has a separate API for fetching comments history, then commentRevision can be null |
|                     | linkRevision           | Object   | Returns the list of links that existed in the entity in the previous revision in oldValue.In newValue, send a list of existing links as of this revision. <br> If no link was added, deleted or modified in this revision OR the end system has a separate API for fetching link history, linkRevision can be null |
| nextPageLink        |                        |          | Link to the next page of the entity history response. <br> The connector should return the link of the next page exactly in the same way as it is returned from the end system. This is an optional field.<br> If the end system does not provide next page link in the list API, it can remain null. |






