## Description

When you encounter error OH-JIRA-0232, then following error message will appear:
 **Error: OH-JIRA-0232**: Error occurred while getting details for fields [customfield_xxx]

Where `xxx` is an internal id of custom field in JIRA.

## Cause

While creating or updating an entity type in a particular project in JIRA, if this field is not available in appropriate (create/edit) screen, JIRA API won't be able to set value for this custom field. 

## Solution

For solving this issue, add the field in the appropriate screen. Follow the steps in  
[Field Helper in Jira](../../../../connectors/jira.md#field-helper) to know how to add the field in the appropriate screen.
