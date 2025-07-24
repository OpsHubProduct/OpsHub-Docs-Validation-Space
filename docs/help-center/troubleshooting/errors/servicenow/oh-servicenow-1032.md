# Description

OH-ServiceNow-1032: Error occurred while executing criteria query &lt;query&gt;. Please check the criteria configured. The query must be in the ServiceNow REST table API syntax. Please check the documentation for syntax.

# Cause

Criteria query that is configured in Integration Criteria Configuration section is not correct.

# Solution

* Open integration for which this error has occurred.
* Navigate to configure criteria section of the entity for which this error has occurred.
* Correct the query configured in integration.

For the syntax of criteria query, please refer [ServiceNow Criteria Configuration](../../../../connectors/servicenow.md#criteria-configuration)

For steps on how to configure criteria, please refer [Criteria Configuration](../../../../integrate/integration-configuration.md#criteria-configuration)
