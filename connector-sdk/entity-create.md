# Overview
This API is supposed to create a new entity in the end system and return the entity object as a response. As part of the request payload, OpsHub will send all the field details with which entity needs to be created. Therefore, API must set only the values that are coming and shouldn’t modify or add any more fields while creating an entity in the end system.

# API URI
This is the URI, OpsHub will execute to call this API:  

```http
POST: /entities/{entityTypeId}?
projectId=<projectId>
```


# Request Payload
```json
{
  "fields": {
    "<field1>": "field1_value",
    "<field2>": [
      "field2_Value1",
      "field2_value2"
    ],
    "<field3>": true,
    "<field4>": 1000,
    "<userField>": "userName"
  },
  "mandatoryLinks": [
    {
      "<linkTypeField>": "",
      "<linkedEntityIdField>": "",
      "<linkedEntityTypeField>": "",
      "<linkedEntityScopeIdFieldName>": ""
    }
  ]
}

# URI Parameters

| Name         | In     | Required | Type   | Description |
|--------------|--------|----------|--------|-------------|
| entityTypeId | path   | True     | String | Type of entity that need to be created |
| projectId    | Query  | True     | String | Project in which entity need to be created |

# Request Body

| Name           | Required | Type   | Description |
|----------------|----------|--------|-------------|
| fields         | True     | Object | It will contain name: value pair for all fields that need to be set while creating an entity in the end system, where (name) is the field id of the field to be set and (value) contains the value that needs to be set. For multi-select fields, the value will be a list of strings. For example, for user-type fields, OpsHub will send a username or email, depending on the data type specified for that field in entity-types API. On the other hand, the value will be a string for other fields like text, number, etc.<br>API must set only the values that are coming and shouldn’t modify or add any more fields while creating an entity in the end system |
| mandatoryLinks | False    | Object | It will contain only mandatory links that need to be set as part of creating an entity.<br>Note: It won’t contain non-mandatory links. For adding non-mandatory links, a separate add-link API will be called.<br>Note: API must only link to mandatory links coming as part of the request payload and should not add any other link. |

# Response Payload

Please refer to the [Response Payload](entity-getet#response-payload) section of the Entity-Get API.
