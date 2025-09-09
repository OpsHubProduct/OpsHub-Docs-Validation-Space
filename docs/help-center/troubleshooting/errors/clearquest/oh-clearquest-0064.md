## Description

When the user encounters OH-ClearQuest-0064, the following type of error message will appear:

OH-ClearQuest-0064: Invalid Filter `<Filter Fields Name>` encountered for the query `cq.query:Personal Queries/OpsHub_<QueryName><EntityName>`. Expected filter(s) are `<Filter Fields Name>`.

Example:
:: OH-ClearQuest-0064: Invalid Filter Owner.login_name encountered for the query `cq.query:Personal Queries/OpsHub_LastCreatedByIntegration<EntityName>`. Refer OIM product guide for more details on this query configuration. Expected filter(s) are [history.user_name, history.action_timestamp, history.old_state]

## Cause

*This issue occurs when upgrading {{SITENAME}} to version 7.78 or higher. It throws event failure as the query filters format is changed.*  
*The **query filters** for the particular query are not correctly selected.*

## Solution

Update the **query filters** as mentioned in the IBM ClearQuest Rational connector documentation. Refer to the [Queries Configuration](../../../../connectors/ibm-rational-clearquest.md#queries-configuration) section.
