## Description

When you encounter error OH-JIRA-0221, then following error message will appear:

> OH-JIRA-0221: Either username, password or both provided for JIRA system are invalid or you do not have sufficient permission(s). Please provide the correct credentials and verify your access level. The status code received from server is: 401.

## Cause

Probable causes for this issue are:  
1. Either username, password or both provided for JIRA system configuration is incorrect.  
2. User doesn't have required privileges in Jira for making this particular REST API request.

## Solution

1. To check whether the username or password provided in system configuration is correct or not, perform these steps:  
   1. Login with the same username and password through the Jira UI.  
   2. If the login was not possible through Jira UI, please check with your administrator for correct credentials.  
2. For checking whether the user has required privileges/sufficient permission(s), please check whether these prerequisites are followed: [Prerequisites for sync user in Jira](../../../../connector/jira.md#prerequisites)
