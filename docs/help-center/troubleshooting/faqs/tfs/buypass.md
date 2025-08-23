## Description

During system configuration, there is an option to set the ByPass rule option. By default, the option is set to "No". There are use cases when this option can be set to "Yes".

## Solution

Following are the use cases when ByPass option is used:

* **Ignore rules/validations:** This will allow users to write invalid value(s) to any field in the system.  
  For example, the **State** field contains only two states: "Active" and "Closed". If the user wants to write an invalid value in state (e.g., "New"), that is possible.  
  Another example: a rule is configured that the **Description** field should not be empty when the **State** field changes to "Active". This kind of rule can be ignored if ByPass option is set to "Yes".

* **User Impersonation:** A user can create/update a work item by a different user than the Integration user.  
  If ByPass Rule is set to "No", the work item is created/updated by the Integration user.  
  If ByPass is set to "Yes", the user can configure the integration so that a work item is created by the original audit user.  
  In short, configuration of **Changed By** or other user fields in audit/history can be changed by enabling ByPass.

* **Date ByPass:** Ignore the date validation and create/update a work item at the same time as it is created in the source.  
  This means a user can create/update a work item with a past date using the ByPass option.  
  In short, a user can change **Changed Date** or other date fields in audit/history by enabling ByPass.

Refer table under [Team Foundation Server - Common](../../../../connectors/team-foundation-server.md#known-behaviors-and-limitations) section to check which all fields are supported with and without ByPass with different API options.

