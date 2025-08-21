### Overview
API should add a new comment in a given entity id in the end system.

### API URI
This is the URI OpsHub will execute to call this API:

```http
POST: /entities/{entityTypeId}/{entityId}/comments? 
      projectId=<projectId>
```

### URI Parameters

| Name | In | Required | Type | Description |
|------|----|---------|------|-------------|
| entityTypeId | path | True | String | ‘id’ of the entity type for given entityId |
| entityId | path | True | String | ‘id’ of the entity in which comment need to be added |
| projectId | query | True | String | Project in which the given entity exists |

### Response Payload

```json
{
  "<comment title Field>": "",
  "<comment body Field>": "",
  "<comment Type Field>": ""
}
```

### Request Body

| Name | Required | Type | Description |
|------|---------|------|-------------|
| `<comment title Field>` | True | String | The name will be the field name of the comment title, as passed in entity-type configuration API. The value will be the text that needs to be set in the comment title |
| `<comment body Field>` | True | String | The name will be the field name of the comment body, as passed in entity-type configuration API. The value will be the text that needs to be set in the comment body |
| `<comment Type Field>` | False | String | If there are different types of comments, then OpsHub will pass the type of comment that needs to be added |

### Response Payload

API should add a new comment and return the comment id and date on which it got added.

```json
{
  "<comment id Field>": "",
  "<comment created Date Field>": ""
}
```

### Response Parameters

| Name | Required | Type | Description |
|------|---------|------|-------------|
| `<comment id Field>` | True | String | The name will be the field name of comment id, as passed in entity-type configuration API. The value will be the id of the comment that just got added |
| `<comment created Date Field>` | True | Date | The name will be the field name of the comment created date, as passed in entity-type configuration API. The value will be the time at which the comment got added |

