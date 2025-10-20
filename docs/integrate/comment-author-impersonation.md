# Overview

- **<code class="expression">space.vars.SITENAME</code>** supports the comment author impersonation, where the comment from the source system will be synced to the target system along with the comment author.

- For an example:
  1. Integration is configured for Epic entity from Jira to Azure DevOps. The Azure DevOps synchronization user has the required permission to perform the user impersonation.  
  2. **User 1** added one comment in Jira Epic. As a part of the sync, the comment will be added to Azure DevOps via **User 1** (instead of the **<code class="expression">space.vars.SITENAME</code>** sync user).

## Supported systems

- Azure DevOps Services and Team Foundation Server  
  - Please refer to [Team Foundation Server](../connectors/azure-devops) to learn about the required permissions for impersonating comment author.

## Configuration

- Enable the comment sync in the **<code class="expression">space.vars.SITENAME</code>** mapping. As a result, the comment sync will enable the comment's author impersonation without any additional configuration.

