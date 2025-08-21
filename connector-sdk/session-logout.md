# Overview
Logs out of the end system and cleans up any cached data for the given SDK session id. This API will be called by OpsHub, only at the end once all sync events are processed. 

# API URI
This is the URI, OpsHub will execute to call this API: 

```http
POST: /cleanup/{sdkSessionId}?systemId=<systemId>&cleanupGlobalCache=<cleanUpGlobalCache>
```

Request headers will contain all the key-value data returned from the Initialize API for the given session id.  

# URI Parameters

| Name | In | Required | Type | Description |
|------|----|----------|------|-------------|
| sdkSessionId | Path | True | UUID | Unique ID to distinguish each session. SDK can use this session id to cache any information for a specific session. |
| systemId | Query | False | String | Unique Id that identifies the integration system and can be used by the SDK to maintain a global cache or session-related data for that specific system. |
| cleanupGlobalCache | Query | False | Boolean | Specifies whether to clean up the global cache associated with the given **systemId**. <br/><br/>If set to **true**:<br/>– Indicates that the system configuration has changed or been refreshed.<br/>– SDK should delete all cached or persistent data related to the specified **systemId**.<br/>– Ensures that fresh data is loaded.<br/><br/>If set to **false** (or not provided):<br/>– SDK may retain global cache and only clean up data related to the current session. |

# Response
200 OK
