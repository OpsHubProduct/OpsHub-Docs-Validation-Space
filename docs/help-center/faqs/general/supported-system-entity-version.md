## Description

There can be multiple queries as below: 

1. How do I know whether a system will be supported or not?

{% if "OpsHub Migrator for Microsoft Azure DevOps" === space.vars.SITENAME %}     
2. If I have one system configured already and I want to upgrade that system to a newer version; how would I know whether the newer version of that system is still supported or not?

{% elif "OpsHub Integration Manager" === space.vars.SITENAME %}  
2. If I have one system integrated already and I want to upgrade that system to a newer version; how would I know whether the newer version of that system is still supported or not?  

{% endif %}

3. How would I know whether a specific entity type of the system is supported or not? 

## Solution

To know which systems, versions, and entity types are supported by <code class="expression">space.vars.SITENAME</code>, refer to the [Systems Supported List](../../../supported-connectors/systems-supported.md) documentation.
