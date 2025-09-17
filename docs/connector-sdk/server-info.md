# Overview
API to get server configuration.

# API URI

```bash
GET:  /server-info
```

# Responses

| Parent Parameters       | Name                 | Required | Type    | Description |
|-------------------------|--------------------|----------|---------|-------------|
|                         | timeZone            | False    | String  | Timezone of the end system. E.g., "America/Los_Angeles" or "GMT-8:00" or "GMT-08:00". Return blank if timezone is embedded in date value. |
|                         | locale              | False    | String  | Locale of the end system. E.g., en-US, en-IN, etc. Note that hyphen (-) is used as separator of language and country. Return blank if timezone is embedded in date value. |
|                         | maxResults          | True     | Integer | The maximum number of records that can be returned from a paginated API in a single page. If end system does not support pagination, connectors can implement in-memory pagination and provide maximum number of items per page in this field. |
| integrationUserInfo     |                     | True     |         |             |
|                         | fieldInternalName   | True     | String  | Internal name of the field used on system configuration screen to take integration username or email. This field name should match with the field name provided in connector metadata API. |
|                         | userDataType        | True     | Enum    | Data type of integration user taken as input in fieldInternalName. Valid values are: <br/>- EMAIL_AS_USER: When email is provided in the integration user field. <br/>- USERNAME_AS_USER: When username is provided in the integration user field. |

# Response Payload

```json
{
  "timeZone": "UTC",
  "locale": "en-US",
  "maxResults": 50,
  "integrationUserInfo": {
    "userDataType": "USERNAME_AS_USER, EMAIL_AS_USER",
    "fieldInternalName": "userName"
  }
}

```



