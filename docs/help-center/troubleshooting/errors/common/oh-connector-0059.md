## Description

When the user encounters **OH-Connector-0059**, then following error message will appear:  
**OH-Connector-0059**: Error occurred while processing entity, because &lt;&lt;Link Type&gt;&gt; link is mandatory for &lt;&lt;Entity Name&gt;&gt;. Either it is not configured in issue relationship panel or configured link entity is not found.

**Example:**  
OH-Connector-0059: Error occurred while processing entity, because Parent link is mandatory for task. Either it is not configured in issue relationship panel or configured link entity is not found.

## Cause

For some entity types, having a Parent/Dependent entity is required to create the entity in end System. With the same alignment, when {{SITENAME}} is trying to create an entity in such system, the {{SITENAME}} would expect the Parent/Dependent entity should be available. In case such Parent/Dependent entity is not present/found in the target end system, user would receive such processing failure.

**For example:**  
Let's assume we have configured an integration for Task entity with Clarity being the target end point. Now in Clarity, Task can't be created without Project. So while synchronizing Task, if there is no specification of Project (under which this task is to be created) then user would receive a processing failure.

## Solution

User needs to configure link in relationship mapping. For configuring relationship mapping, user should refer to [relationship mapping configuration](../../../..//mapping-configuration.md#relationships).
