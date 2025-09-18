# API Name
**Link – Create or Update**

## Overview
Adds a new link in the given entity ID or updates an existing link.  
"Update link" will happen only for **mandatory links** or for **link types** where only one entity can be linked (for example, Parent).

---

## API URI
```bash
POST: /entities/{entityTypeId}/{entityId}/links?projectId=<projectId>
```

## URI Parameters

| Name         | In    | Required | Type   | Description                                                        |
|--------------|-------|----------|--------|--------------------------------------------------------------------|
| entityTypeId | path  | True     | String | ‘id’ of the entity type for the given entity id                    |
| entityId     | path  | True     | String | ‘id’ of the entity in which links need to be added                 |
| projectId    | query | True     | String | Project in which the given entity exists                           |

---

## Request Payload

```json
{
  "linkType": "",
  "links": [
    {
      "<linkedEntityIdField>": "",
      "<linkedEntityTypeField>": "",
      "<linkCommentField>": "",
      "<externalLinkUrlField>": "",
      "<isExternalLinkField>": "true / false String",
      "<property1>": "value1",
      "<property2>": "value2"
    },
    {
      "<linkedEntityIdField>": "",
      "<linkedEntityTypeField>": "",
      "<linkCommentField>": "",
      "<externalLinkUrlField>": "",
      "<isExternalLinkField>": "true / false String",
      "<property1>": "value1",
      "<property2>": "value2"
    }
  ],
  "rankInfo": {
    "siblingEntity": {
      "internalId": "",
      "entityType": "",
      "scopeId": ""
    },
    "rankOperation": ""
  }
}
```

## Request Body

| Name     | Required | Type   | Description |
|----------|----------|--------|-------------|
| **linkType** | True | String | The type of link for which links are to be added. E.g., `Parent`, `Child`, `Related`.<br><br>**Note:** This is only applicable when connector supports rank feature:<br> - If connector supports rank and rank order type (given in [Entity Type – Get](entity-type-get.md) API's `links.rank.orderType`) is either `HIERARCHY_SINGLE` or `HIERARCHY_MULTIPLE`, connector will need to handle additional link types `Hierarchy Parent` and `Hierarchy Child`. |
| **links** | True | List | List of links to be added.<br>Each link in the list will have its properties as described below:<br>```json { "<linkedEntityIdField>": "The name will be the field name in which entity of the linked entity will come, and the value will be the entity id to which entityId coming in request URI need to be linked", "<linkedEntityTypeField>": "The name will be the field name in which entity type of linked entity will come, and the value will be the entity type of linked entity id", "<linkCommentField>": "Any comment that needs to be added in the link section. Note: This is not a regular entity comment. Some connectors support having a separate note, i.e., a field with each link", "<externalLinkUrlField>": "The name will be the field name in which the external URL will come. The value will be the URL of the external link that needs to be added", "<isExternalLinkField>": "The name will be a field name describing whether a link is internal or external. The value will be True if an external link needs to be added, in which case, the connector only needs to add the link coming in the externalLinkUrlField field. If false, then a regular link to linkedEntityId needs to be added", "<property1>": "Any additional property that connector wants to set while adding or updating the link. Such properties can be passed from the mapping interface in OpsHub", "<property2>": "Any additional property that connector wants to set while adding or updating the link. Such properties can be passed from the mapping interface in OpsHub" } ``` |
| **rankInfo** | False | Object | Only applicable when connector supports rank feature.<br>For move operations `MOVE_BEFORE`, `MOVE_AFTER`, and `MOVE_BULK_AFTER`, `siblingEntity` will also be provided.<br><br>Consider sibling entity as a reference entity to move the current entity before or after that.<br>```json { "siblingEntity": { "internalId": "", "entityType": "", "scopeId": "" }, "rankOperation": "MOVE_BEFORE/MOVE_AFTER/LAST_IN_LIST/MOVE_BULK_AFTER" } ``` |

---

## Response Payload

Returns all the details of links added by the connector.

```json
[
  {
    "<linkTypeField>": "",
    "<linkedEntityIdField>": "",
    "<linkedEntityTypeField>": "",
    "<createdDateField>": "",
    "<createdByField>": "",
    "<linkCommentField>": "",
    "<externalLinkUrlField>": "",
    "<isExternalLinkField>": "true / false String",
    "<property1>": "value1",
    "<property2>": "value2"
  },
  {
    "<linkTypeField>": "",
    "<linkedEntityIdField>": "",
    "<linkedEntityTypeField>": "",
    "<createdDateField>": "",
    "<createdByField>": "",
    "<linkCommentField>": "",
    "<externalLinkUrlField>": "",
    "<isExternalLinkField>": "true / false String",
    "<property1>": "value1",
    "<property2>": "value2"
  }
]

```
