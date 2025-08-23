## Description

During system configuration, there is a field where user needs to enter the Service URL. Now what does {{SITENAME}} accept in the Service URL field.

## Solution

Service URL is a mandatory field during system configuration that is used to provide OpsHubTFSService URL. {{SITENAME}} requires OpsHubTFSService to communicate with Team Foundation Server (TFS) and Azure DevOps.  

Refer [Why {{SITENAME}} needs OpsHubTFSService?](why-sitename-needs-opshubtfsservice) section to learn more about OpsHubTFSService.  

You need to register OpsHubTFSService before providing URL in Service URL field. Refer [How to register OpsHubTFSService?](how-to-register-opshubtfsservice) to learn about how to register OpsHubTFSService.  

By default, OpsHubTFSService is registered on port number `9090`, but in case you want to register on a different port, then refer [How to change default OpsHubTFSService port number?](how-to-change-default-opshubtfsservice-port-number).
