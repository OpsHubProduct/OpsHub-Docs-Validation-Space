## Overview
Returns the connector discovery details.

When registering a connector in OIM, OIM will call this API for each registered SDK API Base URL to ensure that the URL points to an SDK implementation. In case of load balancing, you can host the same SDK connector on multiple servers and register each server URL in OIM. OIM will verify if each registered SDK API Base URL has the same discovery details, i.e., the same `connectorName` and `connectorVersion`.

## API URI
OpsHub will execute the following API:

```http
GET: /discover
```

## Response Payload

```json
{
  "connectorName": "Jira",
  "connectorVersion": "1.0.0"
}
```

## Response Parameters

| Name | Required | Type | Description |
|------|---------|------|-------------|
| connectorName | True | String | Name of the connector implementation. It can be the name of the end system for which the SDK is implemented. |
| connectorVersion | True | String | Version of the connector implementation. Version can be incremented each time a new feature is implemented in SDK, and it is being used for integration in OIM at the same time. |
