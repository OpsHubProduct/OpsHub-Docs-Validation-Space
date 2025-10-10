
## For Team Foundation Server [TFS On-Premise]

* **When TFS System is to be configured with 'Basic Authentication' in <code class="expression">space.vars.SITENAME</code>**
  * If TFS Server Version is >=2015, the IIS setting for **Basic Authentication** needs to **Enable**, for the steps to enable basic authentication on IIS, please refer [this](https://docs.microsoft.com/en-us/iis/configuration/system.webserver/security/authentication/basicauthentication#how-to)
  * **Note**: If we use Basic Authentication and this option is **Disabled** in the IIS Manager, then you might receive a processing failure of 'Unauthorized Access'.
* **When TFS System is to be configured with Personal Access Token in <code class="expression">space.vars.SITENAME</code>**
  * The IIS setting for **Basic Authentication** needs to be kept **Disabled**.
  * **Note**: If we use Personal Access Token and **Basic Authentication** option is **Enabled** in the IIS Manager, then you might receive a processing failure of 'Unauthorized Access'.
  * Please refer [this](https://docs.microsoft.com/en-us/azure/devops/integrate/get-started/authentication/iis-basic-auth?view=azure-devops) link for more information
