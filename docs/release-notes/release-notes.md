{% if "OpsHub Integration Manager" === space.vars.SITENAME %}
# New Version(s)
- **Java Development Kit (JDK):** 17.0.16
- **Tomcat:** 10.1.44
- **Aras Innovator:** Release 35

# Enhancements

## Common
- Failure notification has been enhanced to support waiting until a global error occurs N times before sending a notification.  
  - For details on how to configure the error count before a notification is sent, refer to the [Register for Failure Notification](../help-center/troubleshooting/configure-post-failure-notification.md#register-for-failure-notification) section in the product guide.  
  - This configuration helps reduce unnecessary notifications caused by temporary issues, such as connection resets or timeouts.
- Added support for Activate, Inactivate, and Execute operations based on direction for integration groups.
- Improved link operations to reduce redundant logging during link relationship processing.

## Azure DevOps Services
- Added support for Markdown for rich text fields.  
  - For detailed configuration instructions, refer to the connector guide under [Configuring Rich Text Field Format](../connectors/azure-devops#configuring-rich-text-field-format-for-write-operations).

## Tricentis qTest
- Added support for Check and Create operations for Modules in qTest.  
  - For detailed configuration instructions, refer to the connector guide under [Synchronizing Requirements and Test Cases within a Module](../connectors/tricentis-qTest.md#requirement-and-test-case).

# Major Bugs

## IBM Rational DOORS
- Resolved an issue where a connection reset error occurred due to the DXL script exceeding the character limit.  
  - **Use case:** When IBM Rational DOORS is configured as the source system, <code class="expression">space.vars.SITENAME</code> retrieves data for mapped fields along with the field used for target lookup. Due to improper handling of duplication, the target lookup field was being added repeatedly, even if it was already in the list, causing the DXL script to exceed the character limit.

## Jira Data Center/Cloud
- Resolved an issue where linking operations for archived items were not being skipped if the linked item belonged to a different project in the end system.
- Resolved an issue where relationship mapping in <code class="expression">space.vars.SITENAME</code> displayed reversible link types that are not allowed in the end system.  
  - **Example:** For the Test Plan entity in Xray, the allowed links in the end system are `tests` and `testExecutions`. However, <code class="expression">space.vars.SITENAME</code> also displayed the reverse link `testPlans`, which should only be configured from Tests or Test Executions. If a user mapped the `testPlans` link under the Test Plan entity, it would result in an error, as this link type was not permitted for that issue type in the end system.  
  - **Action:** If such invalid link types are mapped in <code class="expression">space.vars.SITENAME</code>, they must be removed according to the steps in the [post-migration checklist](../manage/upgrade/post-migration-checklist.md#update-relationship-mapping-for-jira).

{% endif %}