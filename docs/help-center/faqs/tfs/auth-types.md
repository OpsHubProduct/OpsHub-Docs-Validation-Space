## Description

Out of the multiple authentication modes supported by Team Foundation Server (TFS)/Azure DevOps, <code class="expression">space.vars.SITENAME</code> supports 2 modes.

## Solution

Following are the authentication modes that are supported by <code class="expression">space.vars.SITENAME</code> for Team Foundation Server (TFS)/Azure DevOps:

* **Basic**  
  * For Team Foundation Server (TFS), **Basic** authentication requires UserName prefixed with Domain Name and Password. For NTLM, **Basic** authentication mode is used.  
  * For Azure DevOps, **Basic** authentication requires Email Id and **Alternative Credentials**. Refer [*Alternative Credentials*](../../../connectors/azure-devops#enable-alternate-authentication-credentials) section to learn how to enable the **Alternative Credentials**.

* **Personal Access Token**  
  * For Azure DevOps, **Personal Access Token** authentication requires Email Id and **Personal Access Token**. Refer [*Personal Access Token*](../../../connectors/azure-devops#create-personal-access-token) section to learn how to create a new personal access token.


