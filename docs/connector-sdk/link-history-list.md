## API Name
Link history – List

## Overview
Returns only the revisions in which the link was added, deleted or modified. This API is handy for the end systems where the end system has a different API for fetching link revision.

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
URI Parameters and Response payload for this API is same as History – List API, with the only difference that this API will return only link revisions. Refer to the [History – List API](history-list.md) page for understanding all the parameters.

## Response Payload
```
{
  "nextPageLink": "// Link to the next page if returned by the end system",
  "nextPageLinkSupported": "true/false | datatype: boolean"
  "revisions": [
    {
      "entityId": "101",
      "revisionId": "1",
      "updatedBy": "username of user who made the change",
      "revisionDateTime": "",
      "revisionType": "CREATE / UPDATE / DELETE",
      "linkRevision": {
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
