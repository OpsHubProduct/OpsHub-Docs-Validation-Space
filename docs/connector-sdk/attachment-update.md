## Overview
Updates an existing attachment in the given entity id.

## API URI
This is the URI OpsHub will execute to call this API:

```bash
PUT: /entities/{entityTypeId}/{entityId}/attachments? 
    attachmentId={attachmentId}& 
    projectId={projectId}
```

## URI Parameters

| Name          | In    | Required | Type   | Description |
|---------------|-------|----------|--------|-------------|
| entityTypeId  | path  | True     | String | ‘id’ of entity type for given entity id |
| entityId      | path  | True     | String | ‘id’ of entity in which attachment needs to be added |
| attachmentId  | path  | True     | String | Id of the attachment that needs to be updated |
| projectId     | query | True     | String | Project in which the given entity exists |

## Request Payload

Multipart/form-data:  

projectId = <projectId>
fileName = <fileName>
file = inputStream
fileComment = <fileComment>


## Request Body

| Name        | Required | Type      | Description                                                                 |
|------------|----------|-----------|-----------------------------------------------------------------------------|
| fileName   | True     | String    | Attachment name to be given when adding the attachment in the end system    |
| File       | True     | Multipart | Base64 encoded stream for attachment content                                 |
| fileComment| False    | String    | Attachment comment to be given when updating attachment in the end system   |

## Response Payload

Return attachment details for the newly added attachment. All the `<keyname>` in the below response will be replaced with the actual field name sent by the connector in the entity-types configuration API.

```json
{
  "idField": "", 
  "contentUriField": "", 
  "renderUriField": "", 
  "fileNameField": "", 
  "contentTypeField": "", 
  "contentLengthField": "", 
  "createdDateField": "", 
  "createdByField": "",
  "fileCommentField": ""
}
```
## Response Parameters

Response parameters are same as Add attachment.  

>**Note**: Id and contentUri should not have ‘::’ double colon.

| Name                | Required | Type     | Description                                                                                                           |
|--------------------|----------|---------|-----------------------------------------------------------------------------------------------------------------------|
| `<idField>`           | True     | String  | The name will be the field name of the attachment id field. The value will be a unique id for the given attachment   |
| `<contentUriField>`   | True     | String  | The name will be the field name of the attachment content URI field. The value will be attachment content URL, attachment id, or anything else that will help the connector later to fetch attachment content only by the given URI |
| `<renderUriField>`   | False    | String  | The name will be the field name of the attachment render URI field. The value will be text to be shown. This field is used to render/display the content of the attachment (e.g., inline image with `<img>` tag). Not used to download the attachment. For downloading, use `contentUri`. |
| `<fileNameField>`     | True     | String  | The name will be the field name of the attachment file name field. The value will be the file name of the attachment added |
| `<contentTypeField>`  | True     | String  | The name will be the field name of the attachment content type field. The value will be the content type of attachment (e.g., IMG, DOC) |
| `<contentLengthField>`| True     | String  | The name will be the field name of the attachment content length field. The value will be the size of the attachment content |
| `<createdDateField>`  | False    | Datetime| The name will be the field name of the attachment created date field. The value will be the date-time at which the attachment was added |
| `<createdByField>`    | False    | String  | The name will be the field name of the attachment created by field. The value will be the username of the user who added the attachment |
| `<fileCommentField>`  | False    | String  | The name will be the field name of the attachment file comment field. The value will be the file comment updated to the attachment |


