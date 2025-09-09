## Description

When the user encounters OH-ClearQuest-0023, the following type of error message will appear:

OH-ClearQuest-0023: Query Parameter(s) not matched, Expected query parameter(s) are `<Filter Fields Name>` for the query Personal `Queries\OpsHub_<Query Name><EntityName>`.

Example:  
:: OH-ClearQuest-0023: Query Parameter(s) not matched, Expected query parameter(s) are [history.user_name, history.action_timestamp, history.old_state] for the query Personal Queries`\OpsHub_LastCreatedByIntegration<EntityName>`.

## Cause

*This issue occurs when upgrading {{SITENAME}} to version 7.78 or higher. It throws event failure as the query filters format is changed.*  
*All the required **query filters** for this particular query are not added to the end-system query.*

## Solution

Update the **query filters** as mentioned in the IBM ClearQuest Rational connector documentation. Refer to the [Queries Configuration](../../../../connectors/ibm-rational-clearquest.md#queries-configuration) section.
