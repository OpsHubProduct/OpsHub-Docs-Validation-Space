## Description

When you encounter error OH-Jama-0041, then following error message will appear:  
**OH-Jama-0041:** Error occurred while executing the request URL: `<URL>` and server response is: `<server response>`. Provided username or password for Jama system are invalid or you do not have enough permissions. Please check and provide correct credential or verify access level.

## Cause

Probable causes for this issue are:

- Either username, password or both provided for Jama system configuration in <code class="expression">space.vars.SITENAME</code> is incorrect.
- User doesn't have required privileges in Jama for making this particular REST API request.

## Solution

- To check whether the username or password provided in system configuration is correct or not, perform these steps:
  1. Login with the same username and password through the Jama UI.
  2. If the login was not possible through Jama UI, please check with your administrator for correct credentials.

- For checking whether the user has required privileges/sufficient permission(s), please check whether these prerequisites are followed:  
  [Prerequisites for synchronize user in Jama](../../../../connectors/jama.md#user-privileges)
