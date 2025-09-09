## Description

When you encounter OH-Connector-0030, then the following error message appears:

**OH-Connector-0030**: Link will not be added. No entity exists in system with global id &lt;global_id&gt;

## Cause

The entity on which failure has occurred is linked to another entity in the source system. Therefore, {{SITENAME}} is trying to set the link relationship on the target side/system as per link mapping. But as the other/linked entity of the source system is not yet synchronized in destination system, this link can't be added and synchronization failed with this error.

This failure occurred as you have selected 'Fail event if linked entity doesn't exist' option in link configuration mapping. For more information on where this option is configured, refer [Mapping Configuration - Relationships](../../../../integrate/mapping-configuration.md#relationships)

## Solution

1. Identify which all link types are configured in field mapping for this integration. To refer current configuration, refer [Mapping Configuration - Relationships](../../../../integrate/mapping-configuration.md#relationships). Based on link relationship configuration, identify which all entities are linked with this failed entity in the source system.  
2. Validate integration to check whether this linked entities from source system are synchronized to target system or not.  
   * If you find that those linked entities are in failure queue, then understand the error and try to fix it. Once this error is fixed, then retry the failure.  
   * If you find that those linked entities are not in failure queue, then validate sync report to confirm that entity is synced or not. For more information on how to see sync report, refer [Integration Sync Report](../../../troubleshooting/integration-sync-report.md)  
     * If you find that linked entity is synchronized as per sync report, then you just need to retry this failure.  
     * If you don't find linked entity in sync report, then make sure that the integration which is configured for linked entity is up and eligible for that linked entity synchronization. Once you validate this action, then execute the integration and wait for the synchronization of linked entity. Once linked entity is synchronized to target system then retry failed event.

For more information on how to retry failed event, refer [Manage Integration Failures - Action on failures](../../../troubleshootingmanage-integration-failures.md#action-on-failures)

