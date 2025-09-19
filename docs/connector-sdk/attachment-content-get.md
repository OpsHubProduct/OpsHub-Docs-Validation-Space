## Overview
Returns base64 encoded stream for the given attachment URI 

## API URI
This is the URI, OpsHub will execute to call this API:

```bash
GET: /entities/{entityTypeId}/attachments/content? 
     projectId=<projectId>    	 
     contentUri=<contentUri>
```
## URI Parameters
| Name         | In    | Required | Type   | Description                                        |
|-------------|-------|----------|--------|---------------------------------------------------|
| entityTypeId | path  | True     | String | ‘id’ of entity type for which attachment content needs to be fetched |
| projectId    | query | True     | String | Project in which the given entity exists         |
| contentURI   | query | True     | String | URI of the attachment for which content needs to be returned |

## Response Payload
Base64 encoded stream – content of an attachment.

