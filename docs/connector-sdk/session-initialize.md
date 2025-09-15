# Overview
SDK can use this API to connect to end system. OpsHub will send all the connection details (e.g., URL, username, password, port, host etc.) user specified in integration, that SDK can use to connect to end system.  

- API will return the parameters which it will need for all subsequent API calls.  
- All the response parameters returned by this, will be passed by OpsHub in subsequent APIs, as Request Headers.  
- When token gets expired, SDK need to pass the appropriate HTTP status code (Refer to [Error Handling](error-handling.md) page). On receiving this error code, OpsHub will again call initialize API to renew the token.

# Recommendations
- When initialize API is called, all the system configuration details are passed in the request. Connector should do necessary validation for the configuration fields. e.g., If a field's value is expected to be a JSON, the JSON value can be validated in this API call.

# API URI
This is the URI, OpsHub will execute to call this API:

# Request Payload

```json
[
  {
    "key": "<endSystemUrl>",
    "value": "https://end-system.com",
    "sensitive": false
  },
  {
    "key": "<userName>",
    "value": "user.name",
    "sensitive": false
  },
  {
    "key": "<password>",
    "value": "password",
    "sensitive": true
  },
  {
    "key": "customParam1",
    "value": "param1Value",
    "sensitive": false
  },
  {
    "key": "customParam2",
    "value": "param2Value",
    "sensitive": false
  }
]

# Request Body

| Name      | Type    | Required | Description |
|-----------|---------|----------|-------------|
| key       | String  | True     | Key will contain name of field input to be taken by end user while creating the System in OpsHub |
| value     | String  | True     | It will contain the value given by the user for that field |
| sensitive | Boolean | True     | Sensitive says if the data is sensitive or not. E.g. password, token will be sensitive |

# Response Payload

```json
[
  {
    "key": "<Authorization>",
    "value": "Bearer fbcf2630-42a1-4094-96db-2ba1d98e1029",
    "sensitive": false
  },
  {
    "key": "<X-endSystemUrl>",
    "value": "https://end-system.com",
    "sensitive": false
  },
  {
    "key": "<X-customParam1>",
    "value": "param1Value",
    "sensitive": false
  }
]

# Response Body

| Name      | Type    | Required | Description |
|-----------|---------|----------|-------------|
| key       | String  | True     | Key can contain any name by which you want to read data later in subsequent APIs. For example, SDK is authenticating to end system using API token and wants OpsHub to pass this token as part of every subsequent API call, then pass token in value, with any name in key, of your choice |
| value     | String  | True     | It will contain the value that you want to use later |
| sensitive | Boolean | True     | If the data passed is sensitive or not. OpsHub will take care not to log such data in logs |

