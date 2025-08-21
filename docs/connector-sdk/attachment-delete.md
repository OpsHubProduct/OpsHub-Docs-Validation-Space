## Overview
Deletes an attachment.

## API URI
This is the URI OpsHub will execute to call this API:

```http
DELETE: entities/{entityTypeId}/{entityId}/attachments? 
attachmentId=<attachmentId>& 
projectId=<projectId>
```

## URI Parameters

| Name           | In    | Required | Type   | Description                                             |
|----------------|-------|----------|--------|---------------------------------------------------------|
| entityTypeId    | path  | True     | String | ‘id’ of entity type for given entity id               |
| entityId        | path  | True     | String | ‘id’ of the entity in which attachment to be deleted  |
| attachmentId    | path  | True     | String | Id of the attachment that needs to be deleted         |
| projectId       | query | True     | String | Project in which the given entity exists              |

## Request Payload
This API does not require a request body. Only HTTP status `204` is returned on successful deletion.
