# Overview

API needs to return field values for a given `entityId`.  
If the `entityTypeId` or `projectId` is passed as `"null"`, then the API must search across the scope and return field values for the given `entityId`.  

OpsHub will call this API to retrieve the **current field values** of a given entity in the end system.

---

## API URI

```bash
GET: /entities/{entityId}?
     entityTypeId={entityTypeId}&
     projectId=<projectId>
     expand=ATTACHMENTS,LINKS (optional)
     fieldList=[fieldList] (optional)
```

## URI Parameters

| Name          | In     | Required | Type         | Description |
|---------------|--------|----------|--------------|-------------|
| **entityId**  | Path   | Yes      | String       | ID of the entity for which the field data needs to be returned. |
| **entityTypeId** | Query | Yes      | String       | `id` of the entity type returned from the Entity Type – List API. |
| **projectId** | Query  | Yes      | String       | Project ID for which the list of entity types is available. Same as the `id` returned by `/projects`. |
| **expand**    | Query  | No       | String       | Controls whether attachments and/or links are included.<br>- If omitted: attachments and links are not loaded.<br>- `expand=ATTACHMENTS`: only attachments returned.<br>- `expand=LINKS`: only links returned. |
| **fieldList** | Query  | No       | List\<String\> | When the connector enables the **MAPPED_DATA_RETRIEVAL** feature, specifies the list of fields to fetch. If omitted or empty, all fields must be fetched. |

---

## Response Payload

> **Note:** This is just a *sample* response payload. All the key names under `fields`, `attachments`, and `links` will differ depending on the field IDs defined in `/entity-types/{entity-type-id}` for the given connector.

```json
{
  "fields": {
    "<field1>": "field1_value",
    "<field2>": [
      "field2_Value1",
      "field2_value2"
    ],
    "<field3>": true,
    "<field4>": 1000,
    "<userField>": "userName",
    "<entityIdField>": "",
    "<entityDisplayIdField>": "",
    "<entityTypeIdField>": "",
    "<projectIdField>": "// required if project based structure",
    "<createdDateField>": "",
    "<updatedDateField>": "",
    "<createdByField>": "",
    "<updatedByField>": ""
  },
  "attachments": [
    {
      "<idField>": "",
      "<contentUriField>": "",
      "<renderUriField>": "",
      "<fileNameField>": "",
      "<contentTypeField>": "",
      "<contentLengthField>": "",
      "<createdDateField>": "",
      "<createdByField>": "",
      "<updatedDateField>": "// Either createdDate or updatedDate is required",
      "<updatedByField>": "",
      "<fileCommentField>": ""
    }
  ],
  "links": [
    {
      "<linkTypeField>": "",
      "<linkedEntityIdField>": "",
      "<linkedEntityTypeField>": "",
      "<linkedEntityScopeIdFieldName>": "",
      "<createdDateField>": "",
      "<createdByField>": ""
    }
  ]
}
```
# Response Parameters

| **Name**      | **Required** | **Type** | **Description** |
|---------------|--------------|----------|-----------------|
| Fields        | True         | Object   | Current field values for all the fields for the entity. E.g., the current value of entity title, summary, status, priority, description, etc.<br>Notes:<br>*All field names should be field id (as sent from `/entity-types/<entity-type-id>` API. Do not use display name of the fields in the API response*<br>*For multi-valued fields, it should only contain list of strings* |
| Attachments   | False        | Object   | Details of the current files attached to the entity |
| Links         | False        | Object   | Details of the entities currently linked to the given entity |

## Examples

1) Sample response for priority field:  
```json
[
  {
    "id": "1",
    "value": "High"
  },
  {
    "id": "2",
    "value": "Medium"
  },
  {
    "id": "3",
    "value": "Low"
  }
]

2) Sample response for priority field with same id and value:

```json
[
  {
    "id": "High",
    "value": "High"
  },
  {
    "id": "Medium",
    "value": "Medium"
  },
  {
    "id": "Low",
    "value": "Low"
  }
]

```
