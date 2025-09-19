## Overview

OpsHub will call this API for fields of type LOOKUP. Implementation of this API should return valid values that the user can set in a given lookup field.

## API URI

```bash
GET: /metadata/fields/{fieldId}/values?projectId=<projectId>&entityTypeId=<entityTypeId>&fieldScope=<FieldScope>
```

## URI Parameters

| Name        | In    | Required | Type   | Description |
|-------------|-------|----------|--------|-------------|
| entityTypeId | path  | True     | String | ‘id’ of entity type returned as response of **Entity Type – List** API |
| fieldId     | path  | True     | String | Id of the field, as sent by Connector SDK from `/entity-types/{entityTypeId}` API |
| projectId   | query | True     | String | Project id for which the list of entity types is available. ProjectId here will be the same as ‘id’ sent as part of `/projects` |
| FieldScope  | query | True     | ENUM   | Scope where Lookup values for a field are to be displayed.<br>- **ENTITY_FIELD**: Provide 'ENTITY_FIELD' when lookup values are to be displayed at mapping level.<br>- **CONFIG_FIELD**: Provide 'CONFIG_FIELD' when lookup values are to be displayed at advanced integration configuration level in entity-level mandatory settings screen. |

## Response Payload

```json
[
  {
    "id": "<id1>",
    "value": "<value1>"
  },
  {
    "id": "<id2>",
    "value": "<value2>"
  },
  {
    "id": "<id3>",
    "value": "<value3>"
  }
]
```

## Response Parameters

| Name  | Required | Type   | Description |
|-------|----------|--------|-------------|
| id    | True     | String | Internal value of the field. For example, for priority field: "low", "medium", and "high". If the end system does not have a different internal name for a field value, pass the display name here too. |
| value | True     | String | Display value of the field. For example, for priority field: "Low", "Medium", and "High". |

# Examples

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
```

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
