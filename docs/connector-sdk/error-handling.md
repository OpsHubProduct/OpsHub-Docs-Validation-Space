*For any API, if error occurs, it should return appropriate HTTP status code. Examples:*  
- **401:** If user is not authenticated or session is expired  
- **403:** If user is authenticated but does not have access to specified resource  
- **404:** If the resource user is trying to access is not available  

*Special handling for error codes:*  
- **HTTP status code 401:** OpsHub will assume that authenticated session has been invalidated and call initialize API to re-login.  
- **HTTP status code 403:** API should return this code when the API rate limit has been reached. OpsHub will wait for the time to come in `<HEADER1>` and resume after that, without failing the sync.  

*Apart from the standard HTTP status code, API should also return the details of the errors if any custom error occurs during the processing of the request.*  
- SDK should send end system code if any is returned from the end system.  
  - For example: If the validation of the request payload is failed, API can return `400 (Bad Request)` response. The error response should also be sent along with the HTTP status.  

# Error Response Payload

```json
{ 
  "errors": { 
    "code": "system-601", 
    "message": "Missing comment title", 
    "detail": "Title of the comment is required" 
  } 
}
```

| **Name** | **Required** | **Description** |
|----------|--------------|-----------------|
| code     | True         | Error code sent by end system or specific code that SDK wants to send |
| code     | True         | Detailed error message as to why API failed |
| detail   | False        | It can contain error details like stack trace, end system response, etc. Anything SDK developer feels that will help the user resolve the error |
