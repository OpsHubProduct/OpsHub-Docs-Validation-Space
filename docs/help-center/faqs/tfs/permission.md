## Description

<code class="expression">space.vars.SITENAME</code> requires one dedicated system user to communicate with the system. This user needs specific permissions. 

## Solution

Dedicated integration user is responsible to read and/or write data from Team Foundation Server (TFS)/Azure DevOps. For these operations, the user needs special permissions. Refer [User Previledges](../../../connectors/azure-devops.md#privileges-for-user) section that explains what all permissions must be given to the integration user.  


