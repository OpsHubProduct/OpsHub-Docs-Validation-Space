## Description

When you encounter OH-TFS/AzureDevOps-0019 then the following error message will appear:

'OH-TFS/AzureDevOps-0019: `<Entity_Type>` with ID `<Entity_Id>` does not exist in the server or integration user does not have the permission to access entity’.

## Cause

One of the probable reasons for this error could be integration user does not have permission to access that entity.

## Solution

Kindly check integration user has sufficient permission(s) for synchronization. Please refer [**User Privileges**](../../../../connectors/azure-devops.md#user-privileges) section and the checklist of required permission that needs to be given to the integration user.
