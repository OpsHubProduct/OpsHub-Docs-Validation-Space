## Description

When you encounter OH-TFS/AzureDevOps-0174, then the following error message will appear: 

'OH-TFS/AzureDevOps-0174: Attempt to add a Link of type `<Link_type>` with Workitem with ID `<Linked_Entity_Id>` is failing due to server error:TF26198: The work item does not exist, or you do not have permission to access it.' 

## Cause

Following are the probable reasons for this: 

* `<Linked_Entity_Id>` has been deleted from the target project after synchronization.
* `<Linked_Entity_Id>` has been moved to another project, which is not accessible by Integration User.

## Solution

* In case <Linked_Entity_Id> has been deleted from the target project, we can process the failure by re-creating entity as follows:
  * Do advance integration setting to re-create deleted entities. Advance integration setting needs to be done for integration that has been configured for entity type of `<Linked_Entity_Id>`. Refer [Action on Entity Deleted in Target](../../../../integrate/integration-configuration.md#action-on-entity-deleted-in-target) section of 'Advance Settings' to learn how to do advanced configuration to re-create entities.
  * Update corresponding linked source entity in the source end system. 
  * Activate Integration to re-create deleted entity.
  * Once deleted entity will be synchronized in target, retry the failure which contains OH-TFS/AzureDevOps-0174 failure.

* In case `<Linked_Entity_Id>` has been moved to another project that is not accessible by Integration User, it can be processed once the Integration User has permission to access the project in which entity has been moved. To give permission to the Integration User, add Integration user in **Project Administration Group**. [Here](../../../../team-foundation-server.md#add-user-in-collection-administration-group) are the steps to add the user in **Project Administration Group**.
