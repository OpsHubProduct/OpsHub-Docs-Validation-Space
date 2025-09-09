## Description

When you encounter error OH-Jama-0040, then following error message will appear:  
**Error message:** OH-Jama-0040: Error occurred while fetching transitions details from Jama. Please provide state transition from external XML file.

Workflow transition is a feature supported by {{SITENAME}} wherein the user can configure {{SITENAME}} to automatically handle workflow transition of an entity as per requirement.

## Cause

Probable cause for this issue is:  
If we have a state transition defined for a field, but related details of Workflow transition are not provided in {{SITENAME}}, then this error occurs.

## Solution

In {{SITENAME}} field mapping configuration, we need to provide the state transition in given format. Refer to [Workflow Transition](mapping-configuration#workflow-transition) for details.
