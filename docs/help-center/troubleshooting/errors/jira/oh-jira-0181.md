## Description
When you encounter OH-JIRA-0181, then following error message will appear:

OH-JIRA-0181: Link Type Parent association is mandatory and should have unique Parent for issue types Sub-Task. Number of Parent links found was &lt;Number of Parent Links found for adding links&gt;

Sample error message:  
OH-JIRA-0181: Link Type Parent association is mandatory and should have unique Parent for issue types Sub-Task. Number of Parent links found was 0

In Jira, for a Sub task type of issue, exactly one parent relation with an another issue type is needed. This error will come up when integration is configured from any source system to Jira for Sub task issue type and <code class="expression">space.vars.SITENAME</code> is trying to create an issue of Sub-Task type in Jira that does not have exactly one Parent relation with any other entity.

## Cause
User might be getting this error due to any of these two possibilities:

**Possibility 1:** In the error message, the user gets 'Number of Parent links found was 0':  
There can be three cases in which such an issue can occur:  
**Case 1:** The configuration is not made for the 'Sub Task Parent' link type in Relationship configuration of corresponding mapping.  
**Case 2:** The configuration is made for the 'Sub Task Parent' link type in Relationship configuration of corresponding mapping, but for the entity in source system, the link was not added.  
**Case 3:** While creating an entity of Sub-Task type, there is not even one parent entity that is recognized by <code class="expression">space.vars.SITENAME</code> found in the target Jira system. This parent entity will be known to <code class="expression">space.vars.SITENAME</code> only if this entity has been polled or created through some integration in <code class="expression">space.vars.SITENAME</code>.

For solving this issue refer to **Solution 1** in the Solution section.

**Possibility 2:** In error message the user gets 'Number of Parent links found was &lt;&lt;Any number greater than 1&gt;&gt;':  
In this case, while creating an entity of Sub-Task type, there is more than one parent entity found in the target Jira system.  
The error could be because of the model mismatch in the Relationship Configuration. The source system is allowing more than one link to be added to the source entity (which is intended to create Sub-Task in target Jira system), but the target Jira system only allows exactly one parent type of relationship for Sub-Task. For solving this issue refer to **Solution 2** in the Solution section.

## Solution

**Solution 1.**  
For solving the issue specified in **Possibility 1** follow these steps:  
**Solving Case1:** User will have to configure 'Sub Task Parent' relationship for Sub-Task type of entity in Jira. For learning how to add 'Relationship Configuration' refer: [Relationships](../../../../integrate/mapping-configuration.md#relationships)  
**Solving Case2:** User might be getting this error because the source entity doesn't have the link mapped with the 'Sub Task Parent' link added to it. Please add the link to the source system entity. After adding the link to the source entity, you can retry the event. For learning how to retry an event, refer: [Manage Integration Failures](../../../troubleshooting/manage-integration-failures.md). After the error is retried, check whether the issue has been resolved by running the integration related to this Sub-Task once again.  
**Solving Case3:** User might be getting this error because the parent entity might have not been synchronized in Jira. Follow the below steps to solve this issue.  
1. Please check whether the integration of the related parent entity of this Sub-Task entity has completed synchronization. Check this through: 'Integration Sync Reports' of the related parent entity. To know more about 'Integration Sync Reports' refer: [Integration Sync Reports](../../../troubleshooting/integration-sync-report.md).  
2. If the parent entity is already synchronized and then the user receives this error message for the Sub-Task integration, there is a possibility that at the time when this Sub-Task was synchronized, the parent entity might not have been synchronized through the parent integration. As the parent integration has now synchronized the entity, this error can be retried. For learning how to retry an event refer: [Manage Integration Failures](../../../troubleshooting/manage-integration-failures.md). After the error is retried, check whether the issue has been resolved when the Sub-Task related integration has ran once again for this Sub-Task entity.

**Solution 2.**  
For the case in **Possibility 2** part of the **Cause**, there needs to be exactly one parent relationship for the Sub-Task. It is an ambiguous case for <code class="expression">space.vars.SITENAME</code> and it cannot take the decision to which parent relationship should be selected for the Sub-Task.  
For solving this model-mismatch scenario, modification can be made in the [Relationship configuration](../../../../integrate/mapping-configuration.md#relationships). The modifications must ensure that user is allowed to select a link type (to be mapped to 'Sub Task Parent' link type) from the available source entity link types for which the source system does not allow more than one such link to be added to the source entity. If the solution is not as per the use-case then please contact us on our support portal for further guidance.

