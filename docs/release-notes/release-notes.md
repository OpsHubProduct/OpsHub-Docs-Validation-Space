{{#ifeq: <code class="expression">space.vars.SITENAME</code> | OpsHub Integration Manager |

# New Version(s)
* Codebeamer: 3.x

# Enhancement

## Azure DevOps Services
* Added support for Service principal authentication types for Pipeline, Areas, Iterations, Test Entities (Test Plan, Test Suite, Test Run, Test Result), Shared Parameter, and Git Commit Information.

## ServiceNow Quick Connect
* Enhanced the update mechanism for ServiceNow items by using PATCH requests instead of PUT, eliminating the need to retrieve the item before updating and thereby reducing unnecessary API calls.

# Major Bugs

## Common
* Resolved an issue where a processing failure occurred with the following error: "com.opshub.eai.core.exceptions.OIMBaseAdapterException: OH-Connector-0055: Error occurred while performing operation on Link of the entity. Caused by java.lang.NullPointerException: Cannot invoke 'java.util.Map.get(Object)' because 'responseMap' is null".
  * **Use Case:** For instance, during integration from the source system to the target system, both Feature and Story entities were being synchronized. If the Feature creation in the target fails and lands in the error queue, but the Story was successfully integrated, it can later be deleted from the source system. This deletion syncs correctly to the target, removing the corresponding Story. However, if the previously failed Feature integration was retried after the story had been deleted, the system throws the above error due to the missing linkage, as it attempted to fetch link information for a linked entity that had been deleted.
* Resolved an issue where a global error with the message "Temporary Lock Acquisition" occurred when multiple integrations were selected and activated simultaneously from the UI, in an environment where OpsHub Integration Manager is installed with an MS SQL database.
* Resolved an issue where the View Relationship XSLT threw an error on the UI when switching from Advanced XSLT back to the Default Configuration.
* Resolved an issue where link properties were not updated in the target system even when the overwrite link setting was enabled.
  * **Use case:** When the source and target links were identical, additional properties—such as the stereotype property (e.g., in Enterprise Architect)—were not evaluated. As a result, if the link already existed in the target, updates to these extra properties were skipped due to a partial comparison.
* Resolved an issue where the error, "IllegalStateException: Transaction already active", was encountered due to transactions remaining open instead of being properly rolled back.
* Resolved an issue where a processing failure occurred with the message: "OH-Connector-06401: Entity type mapping was found in the relationship configuration, which is a license-restricted feature."
  * **Use case:** This issue was observed when OpsHub Integration Manager upgraded directly from version 7.194 or earlier to 7.202 or later, and link relationship mapping was enabled in the configuration. The synchronization process failed due to this restriction.
* Resolved an issue where inline files or attachments were not synchronized correctly when their names contained space characters.

## Aras Innovator
* Resolved an issue where the system returned the error code incompatible_hash_use_md5 with the message: "Incompatible password hash algorithm. Please use MD5."
  * **Use case:** Aras expects user passwords to be submitted in either MD5 hash or plain text formats. However, on the machine where OpsHub Integration Manager was deployed, FIPS (Federal Information Processing Standards) was enabled. This encryption converted plain text passwords to "SHA256 Hash" before they reached the Aras server, resulting in compatibility issues.
  * **Action:** To resolve this error, refer to the [troubleshooting guide](Incompatible_password_hash_algorithm) for appropriate configuration steps.

## Azure DevOps Server
* Resolved an issue where the getEntityRevisions method did not function correctly for Test entities when the Azure DevOps Server version was lower than 2020.

## Digital.ai Agility
* Resolved an issue where a processing failure occurred with the error message: "OH-Agility-0020: Error response from server - Invalid SEL parameter. Unknown token: OH_Comment_External Comment".
  * **Use case:** This issue was observed when Digital.ai Agility was configured as the target system and the "OH Comment" field on the Agility side was mapped from a source field.

## Enterprise Architect
* Resolved an issue where updating a diagram's properties incorrectly modified the diagram image's timestamp, causing unnecessary updates in the target system such as removing and re-adding the attachment.

## Gerrit
* Resolved an issue where an error occurred with the message com.opshub.exceptions.eai.OIMRunTimeException: java.lang.NullPointerException: Cannot invoke 'com.opshub.eai.common.objects.entity.EntityObject.getFields()' while preparing the remote link URL for a change.
  * **Use case:** This error was observed when retrieving the remote link for a change in Gerrit that had multiple entries with the same ID.

## IBM Engineering Test Management
* Resolved an issue where IBM Workflow Management (CCM) links were not retrieved as external links in IBM Engineering Test Management entities.

## Jira
* Resolved a formatting issue observed when using Jira as the target system, where inline attachments or images in rich text fields incorrectly displayed with a trailing "]!".
  * **Use case:** When attachment sync was disabled, inline images or attachments in rich text fields appeared with ]! appended to the attachment name due to an escaping issue during processing.

## Jira Service Management
* Resolved an issue where an error occurred while loading field metadata, resulting in the following exception: "com.opshub.eai.jira.exceptions.OIMJiraApiException: OH-JIRA-0173: Error occurred with status code: 413 in JIRA".
  * **Use case:** When the initial response returned more than 50 records, the subsequent request exceeded Jira Service Management's query size limits, resulting in an HTTP 413 error: "The request could not be satisfied." due to invalid pagination parameters in the API query.

  |

  }}
