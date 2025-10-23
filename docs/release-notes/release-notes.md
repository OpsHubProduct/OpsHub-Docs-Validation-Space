{% if "OpsHub Integration Manager" === space.vars.SITENAME %}

# Enhancement

## Azure DevOps Server/Services
* Added support for retrieving link updates without altering any other fields in Azure DevOps Server (2020 and later) and Azure DevOps Services.

# Major Bugs

## Common
* Resolved an issue where processing failure was observed with message "OpsHub-012021: Error occurred while transforming source xml through XSLT in Mapping File : '<mapping name>' , because of Failed to compile stylesheet. 1 error detected".
* Resolved an issue where the error message "OpsHub-012000: Processing blocked - Processing is already in progress or has failed for the corresponding target entity. This target entity needs to be processed first, and then you may need to retry the failure for entity X." appeared.
  * **Use case:** The error occurred when simultaneous updates happened from both directions. Before the acquired lock in the database was released, a scope change (such as project movement or issue type conversion) in the target system caused the failure
* Resolved an issue where the following processing error was observed during delete job execution: "OpsHub-012418: Error in response. You can check if the entity is present in the end system or check whether it is a valid ID. Error received as: Cannot find object to read."
  * **Use case:** This occurred when an entity was soft-deleted in the target system during delete job execution, but the OpsHub Integration Manager server went down before the marker could be updated. As a result, the recovery process was triggered, and an error occurred while attempting to retrieve attachments for the already-deleted target entity.

## Azure DevOps Server/Services
* Resolved an issue causing processing failures during synchronization of area paths and iterations when the Azure DevOps (as the target system) project was renamed after the initial synchronization.
  * **Use case:** If integration was configured for area paths or iterations and some items were already synchronized to Azure DevOps, renaming the project afterward would result in processing failures when updating the synced area paths or iterations.

## Jira
* Resolved an issue where a processing failure occurred with the following message: "OH-OIM-0011: Error in loading Source Adapter, due to: OH-ConnLoader-0003: Connector for system name: <Jira System Name> could not be instantiated due to OH-JIRA-0173: Error occurred with status code: 403 in JIRA." This error occurred when the Service Management API was invoked.
  * **Use case:** This scenario was triggered when either the service account's access to Service Management projects was revoked or the Service Management plugin license had expired in Jira. If an integration included a Service Management project and a link relationship was configured with Jira as the target system, the system attempted to fetch data using the Service Management API, resulting in the error.

{% endif %}  

{% if "OpsHub Migrator for Microsoft Azure DevOps" === space.vars.SITENAME %}  

# Enhancement
* Added support for retrieving link updates without altering any other fields in Azure DevOps Server (2020 and later) and Azure DevOps Services.

{% endif %}