## Description

{{SITENAME}} requires OpsHubTFSService to communicate with Team Foundation Server (TFS) and Azure DevOps.

## Solution

OpsHubTFSService functioning with {{SITENAME}} can be described as below:

* Team Foundation Server (TFS) and Azure DevOps API work on Object Model API.
* OpsHubTFSService is an intermediate proxy service between Team Foundation Server (TFS)/Azure DevOps and {{SITENAME}}. It is distributed as a part of {{SITENAME}} package.
* {{SITENAME}} makes Team Foundation Server (TFS) and Azure DevOps API call using this proxy service. Using the OpsHubTFSService, {{SITENAME}} reads the data [Work -item details and SCM data] from the Team Foundation Server (TFS) and Azure DevOps as well as {{SITENAME}} writes the data to Team Foundation Server (TFS) and Azure DevOps.
* For SCM data migration, {{SITENAME}} creates a virtual drive with latter on the machine where OpsHubTFSService is installed. OpsHubTFSService downloads the files from the source system that needs be checked in to the target Team Foundation Server (TFS) and Azure DevOps system. These downloaded files would be checked in by {{SITENAME}} using the OpsHubTFSService to the target system.
