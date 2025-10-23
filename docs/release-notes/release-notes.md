{{#ifeq: <code class="expression">space.vars.SITENAME</code> | OpsHub Integration Manager |

# Enhancement

## Common
* Enhanced support for post synchronization with a separate workflow to improve flexibility, maintainability.
  * Please refer to the [Advance Integration configuration](../integrate/integration-configuration.md#workflow-association) for more detailed information.
  * **Recommendation**: After upgrading <code class="expression">space.vars.SITENAME</code>, The synchronization will continue to work without any issues with the existing workflow. However, configuring a dedicated post-sync workflow is recommended to improve flexibility, maintainability, and long-term support alignment.
    * For updating the existing customized workflow, refer to the [post migration](../manage/upgrade/post-migration-checklist.md#separate-workflow-for-post-synchronization.md) checklist.
* Optimized the read operations from Excel files used in Excel lookup within the mapping configuration in <code class="expression">space.vars.SITENAME</code>.

## HubSpot
* Added support for OAuth authentication in the HubSpot Connector.
<code class="expression">space.vars.SITENAME</code>

# Major Bugs

## Common
* Resolved an issue where documentation was missing for users attempting to perform post-registration during silent installation of <code class="expression">space.vars.SITENAME</code> on Linux.

## Azure DevOps Server/Services
* Resolved an issue where incorrect XSLT was generated for the User field when Azure DevOps Server/Services was used as one of the systems in the mapping, in site versions above 7.196.
  * Use case 1: In instances where <code class="expression">space.vars.SITENAME</code> was initially installed with a version prior to 7.196 and later upgraded to a version below 7.206, an issue was observed with existing mappings. If the User field was mapped without any advanced XSLT configuration, saving the mapping would regenerate an incorrect XSLT for the User field.
  * Use case 2: In <code class="expression">space.vars.SITENAME</code> versions above 7.196, newly created mappings would, by default, generate an incorrect XSLT for the User field.
  * **Action**: Upgrading <code class="expression">space.vars.SITENAME</code> to version 7.207 or above will automatically update the incorrect XSLT for the User field to the correct version during the upgrade process.
* Resolved an issue where a global error occurred due to work item type conversion when using Azure DevOps Server/Services as the source system.

## Jira
* Resolved an issue where incorrect XSLT was generated for the User field when Jira was used as one of the systems in the mapping, in site versions above or equal 7.201.
  * Use case 1: In instances where <code class="expression">space.vars.SITENAME</code> was initially installed with a version prior to 7.201 and later upgraded to a version below 7.206, an issue was observed with existing mappings. If the User field was mapped without any advanced XSLT configuration, saving the mapping would regenerate an incorrect XSLT for the User field.
  * Use case 2: In <code class="expression">space.vars.SITENAME</code> versions above or equal 7.201, newly created mappings would, by default, generate an incorrect XSLT for the User field.
  * **Action**: Upgrading <code class="expression">space.vars.SITENAME</code> to version 7.207 or above will automatically update the incorrect XSLT for the User field to the correct version during the upgrade process.
* Resolved an issue where Recovery did not function as expected in Jira Xray integrations. This occurred when different users were configured in the Overwrite section of the advanced integration settings. Specifically, when User X was used for the Jira overwrite configuration, while the Xray Client ID and Secret belonged to User Y.

## ServiceNow Quick Connect
* Resolved an issue where, after upgrading <code class="expression">space.vars.SITENAME</code> to a version above [X], the "Save" button in the integration configuration was disabled for existing integrations using ServiceNow Quick Connect as the source with criteria configured.
  * Use case: In earlier versions, only "In Database" was supported as the storage option for criteria, so the Criteria Storage Type field was not displayed in the UI. In versions above [X], with the introduction of multiple storage options, this field became required—but remained empty by default for older configurations—resulting in the "Save" button being disabled.
* Resolved an issue where an error occurred while fetching lookup values (e.g., Assignment Group) when the name of a lookup value was empty.  
>**Note**:  Going forward, if an empty value is detected in the end system, it will be displayed as `<No name> (sys_id)` in <code class="expression">space.vars.SITENAME</code> when loading lookup values.

## ServiceNow
* Resolved an issue where an error occurred while fetching lookup values (e.g., Assignment Group) when the name of a lookup value was empty.  
>**Note**:  Going forward, if an empty value is detected in the end system, it will be displayed as `<No name> (sys_id)` in <code class="expression">space.vars.SITENAME</code> when loading lookup values.

| 

# Major Bugs
* Resolved an issue where a global error occurred due to work item type conversion when using Azure DevOps Server/Services as the source system.

}}
