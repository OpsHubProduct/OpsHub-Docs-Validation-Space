## API Name
**Get Siblings Under Parent Order By Rank**

## Overview
Applicable only when the end system supports [Rank](../integrate/mapping-configuration#overview-2).

Get all the siblings of an entity identified by the given entity id and under the given parent entity.

Return an empty list if siblings are not available, i.e., the entity is the only entity under the given parent.

**Example:**
```
- Epic1
  - Feature1
  - Feature2
  - Feature3
  - Feature4
    - Story1
    - Story2
  - Feature5
  - Feature6
- Epic2
- Epic3
```

- If the entity id is given for **Feature4** and parent is **Epic1**, siblings should be returned in this order:  
  `Feature1, Feature2, Feature3, Feature4, Feature5, Feature6`

- If the entity id is given for **Epic3** and parent is null, siblings should be returned in this order:  
  `Epic1, Epic2, Epic3`

Parent entity can be null if the given entity id is of a top-level entity.  
E.g., `Epic1`, `Epic2`, and `Epic3` are top-level entities in the above example.


## API URI
```
GET: /api/1.0/entities/{entityTypeId}/{entityId}/links/siblings-under-parent-order-by-rank?
projectId=<projectId>
&parentEntityId=<parentEntityId>
&parentEntityType=<parentEntityType>
```


## URI Parameters

| Name             | In    | Required | Type   | Description |
|------------------|-------|----------|--------|-------------|
| entityTypeId     | Path  | True     | String | ‘id’ of the entity type for the given entity id. |
| entityId         | Path  | True     | String | ‘id’ of the entity for which siblings are requested. |
| projectId        | Query | True     | String | Project in which the given entity exists. |
| parentEntityId   | Query | False    | String | Id of the parent entity under which all the siblings must be found. Will not be passed when the entity is at the root level and has no parent. Will also not be passed when `rankType` is either `FLAT_SINGLE` or `FLAT_MULTIPLE`. |
| parentEntityType | Query | False    | String | Entity type id of the parent entity under which all the siblings must be found. Will not be passed when the entity is at the root level and has no parent. Will also not be passed when `rankType` is either `FLAT_SINGLE` or `FLAT_MULTIPLE`. |


## Response Payload
Response should contain all the siblings ordered by their rank in the end system.  
It should also contain the entity itself.

**Example:**
```json
[
  {
    "internalId": "10001",
    "entityType": "101",
    "scopeId": null
  },
  {
    "internalId": "10002",
    "entityType": "101",
    "scopeId": null
  },
  {
    "internalId": "10003",
    "entityType": "102",
    "scopeId": null
  }
]
```

## Response Parameters

| Name       | Required | Type   | Description |
|------------|----------|--------|-------------|
| internalId | True     | String | Internal id of the entity. |
| entityType | True     | String | Entity type id of the entity. |
| scopeId    | True     | String | The unique identification parameter of an entity. If the entity id is unique across all the projects and entity types, the scopeId can be null. If the entity id is unique under a project but can be repeated in different projects, the scopeId is `projectId`. |
