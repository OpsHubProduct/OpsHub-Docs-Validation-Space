## Description

When you encounter OH-TFS/AzureDevOps-0102 then the following error message will appear:

'OH-TFS/AzureDevOps-0102: Unable to load projects from the server. Error received from the server: TF30063: You are not authorized to access `<TFS_Collection_URL>` Collection. Please check whether the integration user has permission for accessing at least one project in a collection.'

## Cause

Following are the probable reasons for this error: 
* Integration user does not have the permission to access `<TFS_Collection_URL>` collection. 
* Integration user does not have the permission to access any of the projects from `<TFS_Collection_URL>` collection. 

## Solution

* Add Integration user to the collection that you are trying to access. For example, add Integration User to <TFS_Collection_URL> collection. Refer [How to add a user in Collection/Organization](../../../../connectors/azure-devops.md#how-to-add-a-user-in-collection-organization) section for adding user in Collection/Organization.
* Add Integration user to the Project of the collection that you are trying to access. Add Integration user in **Project Administration Group**. Refer [this](../../../../connectors/azure-devops.md#add-user-in-project-administration-group) for adding Integration user in **Project Administration Group**.
* Make sure Integration user has all required permissions. Refer [User Privileges](../../../../connectors/azure-devops.md#user-privileges) for more details.
