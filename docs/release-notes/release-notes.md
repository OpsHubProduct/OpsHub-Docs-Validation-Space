{% if "OpsHub Integration Manager" === space.vars.SITENAME %}


# Critical Updates & Actions Required
## Jira Cloud
* Starting 24 November 2025, Jira Cloud will enforce the "Link Issues" permission requirement for both inward and outward issues during all link operations. Previously, this permission was only required on the outward issue.
  * If the user or service account lacks the necessary permission, an error will be returned during issue creation or updates via the UI, REST APIs, or automation rules.
  * To prevent disruptions, ensure that the "Link Issues" permission is granted to all relevant service accounts across all linked projects.
  * For more details, refer to the [minimal permissions](../connectors/jira.md#user-privileges) required for service accounts.

# Enhancement

## Azure DevOps Server/Services
* Eliminated the dependency on TFS Services for synchronizing test entities such as Test Plan, Test Suite, Test Run, and Test Result—for Azure DevOps Services and Azure DevOps Server (version 2020 and above).
* Added support for retrieving a work item/test entity's history using the utility method `getEntityRevisions`.
>**Note**:  This method enables syncing an item's history into a comment or rich text field in the target system.

## Rally Software
* Optimized the retrieval of Test Case results when Rally Software is the source system.

# Major Bugs

## Common
* Resolved an issue where relationship links were not synchronized to the target system during reconciliation.
  * Use case: This issue occurred when using the "Recreate" option if entity not found or deleted in the target.
* Resolved an issue where outdated data was being used or retrieved even after updating the Excel sheet.
  * Use case: When a user clicked the "Save" button before the Excel upload completed, the updated data was not saved to the database, leading to the retrieval of stale data.
* Implemented file type validation for the Excel upload feature to ensure only supported file formats are accepted.
* Resolved an issue where entity mentions caused processing failures if the mentioned entity belonged to a different project and its entity type was not available in the current project.
  * Use case: In the source Jira, a bug (E1) from project P1 contains a mention of an already synced entity (E2) of type X (e.g., custom type "Request") from another project P2. Since type X does not exist in project P1, attempting to sync the entity led to a processing failure.
* Resolved an issue where global failure notifications were triggered due to multiple jobs executing within a single minute, causing the failure occurrence count to hit the threshold even when the integration scheduler was set to one minute.

## Aha!
* Resolved an issue where valid rich text (HTML) content was not rendered correctly in Aha, despite being well-formed HTML.
  * Use case: In Aha, when a full HTML structure—including `<html>`, `<head>`, and `<body>` tags—was sent, Aha internally stripped these outer tags before processing. However, if the source data included self-closing tags such as `<head/>`, Aha failed to strip them correctly, leading to rendering issues.

## Jira Data Center/Cloud
* Resolved an issue where a comment mention was incorrectly detected as an entity mention, leading to a processing failure.

## Microsoft Dynamics 365
* Resolved an issue where the Case's Internal ID was displayed instead of the Display ID during synchronization to the target system.
  * The internal Id of the case appeared in the configured "Remote ID" field as well as in the sync report within <code class="expression">space.vars.SITENAME</code>.


{% endif %}