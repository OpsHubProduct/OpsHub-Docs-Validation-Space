## Description

When you encounter OH-Connector-0002, then the following error message appears:

**OH-Connector-0002: Entity with internal id `<entity_id>` does not exist.**

## Cause

When you have an existing integration from system A to system B and entity 'E1' is also synchronized from system A to system B. Now, someone deletes 'E1' from system B and someone updates 'E1' in system A. In this case, {{SITENAME}} will not be able to update 'E1' on system B as entity was deleted and therefore, it will fail with this error.

## Solution

1. Validate if entity 'E1' is accidently deleted from system B? If you find, it was accidently deleted, then contact your system administrator to check that whether they can restore the entity in system B. If there is anyway in which the deletion can be annulled, then annull the entity and retry this failure by clicking **'Retry All With Dependents'** option.

2. If you conclude that you can not restore entity 'E1', then refer [Integration Configuration › Action on Entity Deleted in Target](../../../../integrate/integration-configuration.md#action-on-entity-deleted-in-target) documentation to know what other options you have and how to configure these options. **'Create Failure'** is the default option and therefore, you are seeing this failure. Once appropriate option is configured, then retry the failure by clicking **'Retry All With Dependents'** option.

For more information on how to retry failed event refer [Manage Integration Failures › Action on failures](../../../troubleshooting/manage-integration-failures.md#action-on-failures)
