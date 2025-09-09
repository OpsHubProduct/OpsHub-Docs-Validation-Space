## Description

When you encounter **OH-Connector-0174**, then the following error message appears:

**OH-Connector-0174**: Target entity &lt;target_entity_id&gt; corresponding to source entity &lt;source_entity_id&gt; is deleted from target system. As you have selected re-create option in such case, integration will create it again in the next run.

## Cause

When you have an existing integration from system A to system B and entity 'E1' is also synchronized from system A to system B. Now, someone deletes 'E1' from system B and someone updates 'E1' in system A. In this case, {{SITENAME}} will not be able to update 'E1' on system B as entity was deleted and therefore, it will fail with this error. As you have selected 'Recreate' option in cases when target entity is found to be deleted, {{SITENAME}} has failed this event. The reason for this failure is, {{SITENAME}} first reads all the data for that entity and then creates a new entity with all the details. This action requires some processing time and is completed by the next execution cycle.

>**Note**: **'Recreate' option** you may have configured in integration, to see other options refer [Integration Configuration › Action on Entity Deleted in Target](../../../../integrate/integration-configuration.md#action-on-entity-deleted-in-target)

## Solution

No actions required.  
This is a temporary error and it will be automatically resolved in the next execution run. In the next execution run, {{SITENAME}} will create a new entity on system B with proper data and this fail event will be resolved.

