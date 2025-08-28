# oh-tfs-azure-devops-0048

### Description

When you encounter OH-TFS/AzureDevOps-0048, then following error message will appear&#x20;

'OH-TFS/AzureDevOps-0048: Failed to login into the server: `<Server_URL>` with user: `<User_Name>` due to server error `<Server_Error>`

### Cause

Following are the probable reasons for this:

* You are using "On-Premises" deployment and you have not entered correct username or password during system configuration.
* You are using "Cloud" deployment with "Basic" Authentication Mode and you did not enter correct user email and alternative password.
* You are using "Cloud" deployment with "Personal Access Token" Authentication Mode, then the potential reasons could be:
  * Personal Access Token is not correct or not active.
  * Personal Access Token is not created with the organization value "All Accessible Organization".
  * The Personal Access Token is not of Integration user.

### Solution

**Option#1** - If you are using "On-Premises" deployment, then make sure you are using correct username prefixed with the domain name (if any) and password during system configuration.&#x20;

**Option#2** - If you are using "Cloud" deployment with "Basic" Authentication Mode, then make sure you have enabled Alternative Credentials for Integration User and same has provided during system configuration. Click [here](../../../../connectors/team-foundation-server.md#enable-alternate-authentication-credentials) to read how to enable alternative credentials.

**Option#3** - If you are using "Cloud" deployment with "Personal Access Token" Authentication Mode and your Personal Access Token is not Active or not valid, then you can create new Personal Access Token and provide that Personal Access Token during system configuration. Refer [**Personal Access Token**](../../../../connectors/team-foundation-server.md#create-personal-access-token) section to learn how to create a new personal access token.&#x20;
