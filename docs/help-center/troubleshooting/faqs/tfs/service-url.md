## Description

During system configuration, there is a field where user needs to enter the Service URL. Now what does <code class="expression">space.vars.SITENAME</code> accept in the Service URL field.

## Solution

Service URL is a mandatory field during system configuration that is used to provide OpsHubTFSService URL. <code class="expression">space.vars.SITENAME</code> requires OpsHubTFSService to communicate with Team Foundation Server (TFS) and Azure DevOps.  

Refer [Why <code class="expression">space.vars.SITENAME</code> needs OpsHubTFSService?](purpose-of-opshubtfsservice.md) section to learn more about OpsHubTFSService.  

You need to register OpsHubTFSService before providing URL in Service URL field. Refer [How to register OpsHubTFSService?](register-opshubtfsservice.md) to learn about how to register OpsHubTFSService.  

By default, OpsHubTFSService is registered on port number `9090`, but in case you want to register on a different port, then refer [How to change default OpsHubTFSService port number?](register-opsHubtfsservice-other-port.md).

