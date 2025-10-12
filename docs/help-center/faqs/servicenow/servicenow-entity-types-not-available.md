## Description

This behavior is applicable when the desired entity type of ServiceNow is not visible in the mapping/integration configuration screen of OpsHub Integration Manager.

## Cause

The possible reason could be "Import set table" and/or "Transformation map" not being created for the desired entity (which is to be synchronized) for ServiceNow in OpsHub Integration Manager.

## Solution

Configure "Import set table" and "Transformation map" for the entity. For steps, please refer [Import Set and Transformation map](../../../connectors/servicenow.md#configure-import-set-table-and-transformation-map).

As 'Import set table' and 'Transform map' configuration are a part of [pre-requisites](../../../connectors/servicenow.md#prerequisites) for ServiceNow connector, we would advise you to relook into the pre-requisites and fulfill all of them to avoid such issues in the future.

