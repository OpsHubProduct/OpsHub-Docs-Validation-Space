## Description

When you encounter OH-Connector-0043, then the following error message appears:

**OH-Connector-0043**: Unable to find following field in target system : &lt;target field names&gt;. These fields are mapped in mapping but not present in target system and if you want to skip these fields and synchronize the remaining fields then select YES in Skip absent fields in advanced configuration in integration.

## Cause

There can be multiple reasons:

1. <code class="expression">space.vars.SITENAME</code> uses same field mapping for multiple integrations or multiple projects that share common field mapping template. It is recommended to use same mapping for similar fields. Sometimes, the mapped fields may not exists in some projects. Now for those projects if this common field mapping is being used, then <code class="expression">space.vars.SITENAME</code> can fail with this error.

2. Fields are deleted or disabled from the target system/project and therefore <code class="expression">space.vars.SITENAME</code> will not be able to find those fields. It is possible that when the field mapping was setup, these fields were there but later they got deleted or disabled from the target system/project.

## Solution

There are multiple solutions. Choose the one that is suitable to you.

### **Skip Absent Field**

If you want to ignore the fields that don't exists in that target project and keep synchronizing other mapped fields, then choose this option. Please note that once you select this option then <code class="expression">space.vars.SITENAME</code> will not throw any error when such fields won't found in any of the projects for this integration. This option can be configured at the integration level. For more information on how to configure this option, refer [Skip Absent Field](../../../../integrate/integration-configuration.md#skip-absent-field). Once you configure this option, then retry this failure by clicking **Retry All With Dependents** failure option. For more information on how to retry failed event, refer [Action on failures](../../../troubleshooting/manage-integration-failures.md#action-on-failures).

### **Create/Enable missing fields on target project**

If you find that those fields are required for the target project, then contact your system administrator to create/enable those fields on that target project. Once those fields are created in the end system, retry this failure by clicking **Retry All With Dependents** failure option. For more information on how to retry failed event, refer [Action on failures](../../../troubleshooting/manage-integration-failures.md#action-on-failures).

