## API URI

This is the URI, OpsHub will execute to call this API:  

```bash
GET: /entity-types?projectId=<projectId>
```

## URI Parameters

| **Name**     | **In** | **Required** | **Type** | **Description** |
|--------------|--------|--------------|----------|-----------------|
| **projectId** | Query  | True         | String   | Project id for which list of entity types available need to be returned. ProjectId here will be same as ‘id’ sent as part of /projects |

## Response Payload=
```json
[ 

  { 

    "id": "unique identifier for each entity type", 

    "name": "Entity type name that will be visible to user on OpsHub UI", 

          "direction": "SOURCE_ONLY, TARGET_ONLY, BOTH" 

    "pollerType": "CURRENT_STATE, NON_TIME_BASED, ENTITY_WISE_HISTORY" ,

    "isSoftDeleteSupported": "true / false" ,

    "belongsToCategories": "List of Categories in which given Entity Type belongs to" ,

    "projectMovementSupported": "Indicates if movement of the Entity type across projects is supported through API.",

    "isArchiveSupported": "true / false"

  } 

] 
```

## Entity Type Response Parameters
| **Name**               | **Required** | **Type**       | **Description** |
|-------------------------|--------------|----------------|-----------------|
| **id**                  | True         | String         | Internal name of the entity. If end system does not have different internal name for an entity type, pass display name here too. |
| **name**                | True         | String         | Display name of the entity. |
| **direction**           | True         | Enum           | In which direction can we sync the data in end system?<br>- **SOURCE_ONLY**: End system is read only <br>- **TARGET_ONLY**: End system is write only <br>- **BOTH**: End system allows both read and write |
| **pollerType**          | True         | Enum           | Types of poller:<br>- **CURRENT_STATE**: Current state will be synced. Set this pollerType if it is possible from API to query entities based on their create and update time.<br>- **NON_TIME_BASED**: Current state will be synced. Set this pollerType if it is not possible from API to query entities based on their create and update time.<br>- **ENTITY_WISE_HISTORY**: Complete entity history will be integrated. Set this pollerType if the end system has APIs to query history (audits) of entities. |
| **isSoftDeleteSupported** | False      | Boolean        | Set to **true** if end system supports soft delete for the given entity type; else, set it to **false**. |
| **isArchiveSupported**   | False      | Boolean        | Set to **true** if the end system supports archive operation for the given entity type; else, set it to **false**. |
| **belongsToCategories**  | False      | List<String>   | List of categories in which the given entity type belongs. Each category indicates interconvertibility between entity types. |


For instance, if both "Bug" and "Story" are assigned to the "WorkItems" category, it indicates that these two entity types can be converted mutually.  

Category rules:  
- Case-insensitive (e.g., "workitems" and "WorkItems" are treated the same)  
- Max 50 characters per category  
- Allowed characters: A-Z, a-z, 0-9, _  
- Spaces are not allowed  

**Behavior when belongsToCategories is null, empty, or has no other entity types in the same category:**  
- If the list is null/empty or a category has only one entity type, and entity type movement is detected, the old entity type will be marked as deprecated and a new entity with the updated type will be created.  

**Note:** All categories an Entity Type may belong to must be specified. Example:  
- Project1: bug, feature, task, story  
- Project2: requirement, task, testplan  

If movement is detected, entity types must have at least one category in common. |
| **projectMovementSupported** | False | Boolean | Indicates if the movement of the entity type across projects is supported through API.  

**Behavior when projectMovementSupported is false:**  
- If project movement is detected for a category where this is false, the old entity will be deprecated, and a new entity will be created in the new project. |

## Examples

### 1) When Entity Type or Project Movement is not supported

```json
[
  {
    "id": "100",
    "name": "Requirement",
    "direction": "BOTH",
    "pollerType": "CURRENT_STATE",
    "isSoftDeleteSupported": "true",
    "isArchiveSupported": "true"
  },
  {
    "id": "BUG",
    "name": "Defect",
    "direction": "BOTH",
    "pollerType": "ENTITY_WISE_HISTORY",
    "isSoftDeleteSupported": "false",
    "isArchiveSupported": "true"
  },
  {
    "id": "200",
    "name": "Feature",
    "direction": "SOURCE_ONLY",
    "pollerType": "CURRENT_STATE",
    "isSoftDeleteSupported": "true",
    "isArchiveSupported": "true"
  }
]
```

### 2) When Entity Type or Project Movement is supported

**Scenario details:**  

- **Requirement**: Can be converted to Bug and Feature. Can be moved to another project.  
- **Bug**: Can be converted to Requirement only. Cannot be moved.  
- **Feature**: Can be converted to Requirement only. Can be moved.  
- **Test Run**: Cannot be converted. Can be moved.  
- **Story**: Cannot be converted. Cannot be moved.  

**Note:** Bug and Feature cannot be converted to each other as they share no category in common.

```json
[
  {
    "id": "100",
    "name": "Requirement",
    "direction": "BOTH",
    "pollerType": "CURRENT_STATE",
    "isSoftDeleteSupported": "true",
    "isArchiveSupported": "false",
    "belongsToCategories": ["WorkItemsC1","WorkItemsC2"],
    "projectMovementSupported": "true"
  },
  {
    "id": "BUG",
    "name": "Defect",
    "direction": "BOTH",
    "pollerType": "ENTITY_WISE_HISTORY",
    "isSoftDeleteSupported": "false",
    "isArchiveSupported": "true",
    "belongsToCategories": ["WorkItemsC1"],
    "projectMovementSupported": "false"
  },
  {
    "id": "200",
    "name": "Feature",
    "direction": "SOURCE_ONLY",
    "pollerType": "CURRENT_STATE",
    "isSoftDeleteSupported": "true",
    "isArchiveSupported": "false",
    "belongsToCategories": ["WorkItemsC2"],
    "projectMovementSupported": "true"
  },
  {
    "id": "Test Run",
    "name": "Test Run",
    "direction": "WRITE_ONLY",
    "pollerType": "CURRENT_STATE",
    "isSoftDeleteSupported": "true",
    "isArchiveSupported": "false",
    "belongsToCategories": [],
    "projectMovementSupported": "true"
  },
  {
    "id": "Story",
    "name": "Story",
    "direction": "BOTH",
    "pollerType": "CURRENT_STATE",
    "isSoftDeleteSupported": "true",
    "isArchiveSupported": "false",
    "belongsToCategories": null
  }
]
```


