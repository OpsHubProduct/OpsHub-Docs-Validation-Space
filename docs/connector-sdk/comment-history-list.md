# Overview
Returns only the revisions in which a comment was added, deleted or modified. This API is handy for end systems where the end system has a different API for fetching comment revisions.

## API URI
```http
GET: /entities/{entityTypeId}/attachments/history?
     projectId=<projectId>
     &entityId=<entityId>
     &since=<sinceTime>
     &maxTime=<maxTime>
     &notUpdatedByUser=<notUpdatedByUser>
     &startIndex=<startIndex>
     &maxResults=<maxResults>
     &nextPageLink=<nextPageLink>
     &orderByDirection=<orderByDirection>
```

## URI Parameters
URI Parameters and Response Payload for this API are the same as **History – List API**, with the only difference that this API will return only **comment revisions**. Refer to the [History – List API](History_–_List) page for understanding all the parameters.

## Response Payload
```json
{
  "nextPageLink": "// Link to the next page if returned by the end system",
  "nextPageLinkSupported": "true/false | datatype: boolean",
  "revisions": [
    {
      "entityId": "101",
      "revisionId": "1",
      "updatedBy": "username of user who made the change",
      "revisionDateTime": "",
      "revisionType": "CREATE / UPDATE / DELETE",
      "commentRevision": {
        "oldValue": [
          {
            "idField": "",
            "contentUriField": "",
            "fileNameField": "",
            "contentTypeField": "",
            "contentLengthField": ""
          }
        ],
        "newValue": [
          {
            "idField": "",
            "contentUriField": "",
            "fileNameField": "",
            "contentTypeField": "",
            "contentLengthField": ""
          }
        ]
      }
    }
  ]
}
```