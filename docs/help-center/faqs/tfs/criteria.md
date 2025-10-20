## Description

There are the use cases where only a few of the entities that meet a specific condition need to be synchronized instead of all of the entities. <code class="expression">space.vars.SITENAME</code> provides this type of synchronization for TFS/Azure DevOps.

## Solution

Sometimes there are scenarios in which you want to synchronize a few of the entities that meet a specific condition, for example user wants to synchronize entities that contain priority "1". This type of synchronization is possible by <code class="expression">space.vars.SITENAME</code> using Criteria Filter. Refer [Criteria Configuration](../../../integrate/integration-configuration.md#criteria-configuration) section to learn about how to configure criteria during integration configuration. Refer [Criteria Configuration](../../../connectors/azure-devops.md#criteria-configuration) section of Team Foundation Server (TFS) to learn about the syntax of the criteria query while configuring criteria for TFS/Azure DevOps integration.

