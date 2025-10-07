## Description

Personal access tokens (PATs) are used to authenticate into Azure DevOps. PAT needs to be created with required permissions based on entity type which needs to synchronize. 

## Solution

* <code class="expression">space.vars.SITENAME</code> provides multiple ways to authenticate Integration User, one of the type is "Personal Access Token". Refer [Create Personal Access Token](../../../connectors/team-foundation-server.md#cloud-vsts-pat) section to learn about how to create a Personal Access Token.
* Personal Access Token should be created with required permissions. Permissions are vary based on entity type you want to synchronize. Refer [Personal Access Token Minimum Required Permission](../../../connectors/team-foundation-server.md#personal-access-token-minimum-required-permission) section under **User privileges** to learn about which permissions are required.


