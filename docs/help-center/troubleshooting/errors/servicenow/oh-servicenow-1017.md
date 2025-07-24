## Description

OH-ServiceNow-1017: Failed to load look-up values for selected field &lt;field_name&gt; because neither Name nor Number attributes are found in the referenced entity &lt;referenced_entity&gt;.

## Cause

Referenced table of field &lt;field_name&gt; does not contain the fields Name or Number. Or due to ACL restriction, the referenced table is not accessible.

## Solution

* Give required permission to Sync User so that reference table &lt;table_name&gt; of field &lt;field_name&gt; is accessible.
* Do advance mapping configuration for this field if neither Name nor Number attribute are not found in referenced entity.

For details on Synchronizing reference field, please refer [Syncing reference fields](../../../../connectors/servicenow.md#syncing-reference-fields)
