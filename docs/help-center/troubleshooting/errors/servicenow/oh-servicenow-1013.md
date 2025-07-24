## Description
OH-ServiceNow-1013: Not able to get "Import set table" for entity type: &lt;entity_type&gt;. Please Create "Import set table" and Transformation map under OpsHub Integration Manager.

## Cause

"Import set table" and/Or "Transformation map" configurations are not as per the instructions in ServiceNow connector guide.

## Solution

* "Import set table"/"Transformation map" needs to be configured within ServiceNow for integration purpose for every entity that needs to be synchronized.

* For steps to configure the "Import set table" and/or "Transformation map", please refer [Import Set and Transformation map](../../../../connectors/servicenow.md#configure_import_set_table_and_transformation_map)

As 'Import set table' and 'Transform map' configuration are a part of [pre-requisites](../../../../connectors/servicenow.md#prerequisites) for ServiceNow connector, we would advise you to relook into the pre-requisites and fulfill all of them to avoid such issues in the future.
