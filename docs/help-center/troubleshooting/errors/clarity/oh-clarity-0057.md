## Description
When the user encounters **OH-Clarity-0057**, then following error message will appear:  
OH-Clarity-0057: Error occurred while getting 'o_ohLastUpdate' for entity. 'o_ohLastUpdate' attribute is not properly configured in end system as expected. configure 'o_ohLastUpdate' field as per given in "Custom Field Configuration" section of Clarity system in Product Guide.

## Cause
When Clarity system is as target end point, the cause of this issue is that {{SITENAME}} is not able to access field with 'o_ohLastUpdate' API attribute Id or 'o_ohLastUpdate' is not configured for an entity.

## Solution
{{SITENAME}}'s prerequisite is to configure a custom field with API attribute Id with 'o_ohLastUpdate' for an entity which needs to synchronize.  
The user can refer to [Prerequisites  > Custom Field Configuration](../../../../connectors/clarity.md#custom-field-configuration).
