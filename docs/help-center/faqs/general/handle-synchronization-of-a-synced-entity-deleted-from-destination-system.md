
## Description

Integration is configured from system A to system B. User had created an entity in system A that got created in system B through <code class="expression">space.vars.SITENAME</code>. Now user is doing some update on the entity in system A whereas another user had already deleted that entity from system B. In such cases, what will <code class="expression">space.vars.SITENAME</code>do for this update event which came from System A?

## Solution

When there is an event on deleted target entity, by default <code class="expression">space.vars.SITENAME</code>will generate a failure.

To resolve this failure, given below are a few appropriate options:  

1. Recreate the deleted entity on system B.  
2. Skip the update made on respective source entity of system A.  
3. Create a failure. This is a default option. Identify such failures in <code class="expression">space.vars.SITENAME</code>and then delete the failures manually. To manage failure, refer [Manage Integration Failures](../../troubleshooting/manage-integration-failures.md). Please make a note that once you delete such failure from <code class="expression">space.vars.SITENAME</code>, if any update comes on system A after some time, then it will again generate a failure.  

For more information on how to configure above options settings, refer [Integration Configuration – Action on Entity Deleted in Target](../../../integrate/integration-configuration.md#action-on-entity-deleted-in-target).
