## Overview
This API is supposed to soft delete an entity in the end system. OpsHub will call this API to soft delete entity in the end system.

## API URI
```
DELETE: /entities/{entityTypeId}/{entityId}?
     projectId=<projectId>&deletionType=<deletionType>
```

## URI Parameters
| **Name**      | **In**  | **Required** | **Type** | **Description** |
|---------------|--------|--------------|----------|-----------------|
| entityTypeId  | path   | True         | String   | ‘id’ of entity type of the entity to be deleted |
| entityId      | path   | True         | String   | Id of the entity for which the delete operation is to be performed |
| projectId     | Query  | True         | String   | Project id of the project in which entity to be deleted is associated. ProjectId here will be the same as ‘id’ sent as part of /projects |
| deletionType  | Query  | True         | ENUM     | Deletion types as per which delete operation should be performed:<br>- SOFT_DELETE<br>- ARCHIVE |

