# Add Attachment API

## Overview
Adds an attachment to the given entity id.

## API URI
```http
POST: /entities/{entityTypeId}/{entityId}/attachments?projectId={projectId}
```

## URI Parameters

| Name          | In    | Required | Type   | Description                                                  |
|---------------|-------|----------|--------|--------------------------------------------------------------|
| entityTypeId  | path  | True     | String | ID of the entity type for which attachment content needs to be added |
| entityId      | path  | True     | String | ID of the entity in which attachment needs to be added      |
| projectId     | query | True     | String | Project in which the given entity exists                    |

## Request Payload
Content-type: `multipart/form-data`

- `fileName` = `<fileName>`  
- `file` = `inputStream`  
- `fileComment` = `<fileComment>`

## Request Body

| Name        | Required | Type      | Description                                         |
|-------------|----------|-----------|-----------------------------------------------------|
| fileName    | True     | String    | Attachment name to be given when adding attachment in the end system |
| File        | True     | Multipart | Base64 encoded stream for attachment content       |
| fileComment | False    | String    | Attachment comment to be given when adding attachment in the end system |

## Response Payload

Return attachment details for the newly added attachment. All the `<keyname>` in the response will be replaced with the actual field name sent by the connector in the entity-types configuration API.

```json
{ 
  "<idField>": "", 
  "<contentUriField>": "", 
  "<renderUriField>": "", 
  "<fileNameField>": "", 
  "<contentTypeField>": "", 
  "<contentLengthField>": "", 
  "<createdDateField>": "", 
  "<createdByField>": "",
  "<fileCommentField>": ""
}
```
## Response Parameters

![Note](../assets/Note.jpg) Id and contentUri should not have ‘::’ double colon.

| Name | Required | Type | Description |
|------|----------|------|-------------|
| `<idField>` | True | String | The name will be the field name of the attachment id field. The value will be a unique id for the given attachment |
| `<contentUriField>` | True | String | The name will be the field name of the attachment content URI field. The value will be attachment content URL, attachment id, or anything else that will help the connector later to fetch attachment content only by the given URI |
| `<renderUriField>` | False | String | The name will be the field name of the attachment render URI field. The value will be text to be shown. The field which has value as the URI to render/display the content of the attachment. Note that this URI is not used to download an attachment. For download attachment URI, refer to contentUri. For example, if inline image is shown with `<img>` tag, render uri is the value of the `src` attribute of `<img>` tag |
| `<fileNameField>` | True | String | The name will be the field name of the attachment file name field. The value will be the file name of the attachment added |
| `<contentTypeField>` | True | String | The name will be the field name of the attachment content type field. The value will be the content type of attachment. For example, IMG, DOC, etc |
| `<contentLengthField>` | True | String | The name will be the field name of the attachment content length field. The value will be the size of the attachment content |
| `<createdDateField>` | False | Datetime | The name will be the field name of the attachment created date field. The value will be the date-time at which the attachment was added |
| `<createdByField>` | False | String | The name will be the field name of the attachment created by the field. The value will be the username of the user who added the attachment |
| `<fileCommentField>` | False | String | The name will be the field name of the attachment file comment field. The value will be the file comment added to the attachment |
