## Description

This behavior is applicable when Link type is visible in ServiceNow UI, but you are not able to see it in the Issue relationship section of Mapping.

## Cause

The probable reason could be: A field (corresponding to the link field of the entity) is not created in "Import set table" or not mapped in the "Transformation map" setting for the entity that you are synchronizing.

## Solution

Create/update configuration related to "Import set table" and/or "Transformation map" setting for the link field of the entity that you are synchronizing. For steps, please refer [Configure reference type fields](../../../connectors/servicenow.md#configure-reference-type-fields).

As 'Import set table' and 'Transform map' configuration are a part of [pre-requisites](../../../connectors/servicenow.md#prerequisites) for ServiceNow connector, we would advise you to relook into the pre-requisites and fulfill all of them to avoid such issues in the future.


