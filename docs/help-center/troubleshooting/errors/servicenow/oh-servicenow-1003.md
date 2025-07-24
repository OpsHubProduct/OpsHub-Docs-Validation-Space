# Description
OH-ServiceNow-1003: Error in response from serviceNow server: ServiceNowError \[errorMessage=User not authorized, errorDetails=30 records constrained due to ACL restrictions, status=failure, statusCode=403.\]

# Cause

Sync User does not have the permission(s) to access the REST table API.

# Solution

For integration with ServiceNow, ServiceNow REST table API is used.  
To access table API, Sync User needs permission(s).  

Refer [User Privileges](../../../../connectors/servicenow#user_privileges) to learn about permission(s) required for different tables.
