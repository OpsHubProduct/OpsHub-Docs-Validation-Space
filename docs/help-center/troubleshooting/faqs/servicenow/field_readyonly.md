## Description

This behavior is applicable when a field is editable in ServiceNow UI but it is shown as 'Read Only' in OpsHub Integration Manager in mapping configuration.

## Cause

The reason could be: A field (corresponding to the actual field of the entity) is not created in "Import set table" or it is not mapped in "Transformation map" for the entity which synchronizing is being done.

## Solution

Create/update configuration related to "Import set table" and/or "Transformation map" for the entity that is being synchronized.  
For steps, please refer [Import Set and Transformation map](../../../../connectors/servicenow.md#configure-import-set-table-and-transformation-map).

As 'Import set table' and 'Transform map' configuration are a part of [pre-requisites](../../../../connectors/servicenow.md#prerequisites) for ServiceNow connector, we would advise you to relook into the pre-requisites and fulfill all of them to avoid such issues in the future.
