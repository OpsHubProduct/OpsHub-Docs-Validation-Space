
## Overview
Returns the sequence in which a set of fields needs to be updated. OpsHub will break the incoming payload from the source system accordingly and call the **entity – update API** multiple times, as required to update all fields.  

> **Note:** This API is mandatory to implement if any entity type has `DYNAMIC_SUB_STEPS`.  

## API URI
OpsHub will execute the following API:

```http
POST: /entities/{entityTypeId}/sub-steps-for-update?projectId=<projectId>
```

## URI Parameters

| Name | In | Required | Type | Description |
|------|----|---------|------|-------------|
| entityTypeId | path | True | String | ‘id’ of the entity type for which sub-steps are required |
| projectId | query | True | String | Project for which sub-steps are required |

## Request Payload
Request payload can be constructed using the following structure:

```json
{ 
  "fields": { 
    "<title>": "Title", 
    "<description>": "Description", 
    "<priority>": "High", 
    "<status>": "closed" 
  } 
}
```

## Request Body

| Name | Required | Type | Description |
|------|---------|------|-------------|
| fields | True | Object | Contains name:value pairs for all fields to be sent in subsequent update entity requests, where `name` is the field ID and `value` is the value to update. The API can scan field values to determine how to distribute the fields across multiple update requests if required. |

## Response Payload
The API should return a list of fields to be sent in subsequent requests to update an entity. The order of fields should follow the workflow of the end system.  

> **Example:** If entity fields are being changed and the entity status is being closed, the SDK should first send the group of other fields. Then the status should be sent in a separate list. OpsHub will first call the **entity–update API** to update the other fields and then call the **entity–update API** again to update only the status to `Closed`.

```json
[
  { 
    "fields": { 
      "<title>": "Title", 
      "<description>": "Description", 
      "<priority>": "High" 
    } 
  }, 
  { 
    "fields": { 
      "<status>": "closed" 
    } 
  } 
]
```

