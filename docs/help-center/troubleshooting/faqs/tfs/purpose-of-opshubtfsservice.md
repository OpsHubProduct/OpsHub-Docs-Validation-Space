## Description

<code class="expression">space.vars.SITENAME</code> requires OpsHubTFSService to communicate with Team Foundation Server (TFS) and Azure DevOps.

## Solution

OpsHubTFSService functioning with <code class="expression">space.vars.SITENAME</code> can be described as below:

* Team Foundation Server (TFS) and Azure DevOps API work on Object Model API.
* OpsHubTFSService is an intermediate proxy service between Team Foundation Server (TFS)/Azure DevOps and <code class="expression">space.vars.SITENAME</code>. It is distributed as a part of <code class="expression">space.vars.SITENAME</code> package.
* <code class="expression">space.vars.SITENAME</code> makes Team Foundation Server (TFS) and Azure DevOps API call using this proxy service. Using the OpsHubTFSService, <code class="expression">space.vars.SITENAME</code> reads the data [Work -item details and SCM data] from the Team Foundation Server (TFS) and Azure DevOps as well as <code class="expression">space.vars.SITENAME</code> writes the data to Team Foundation Server (TFS) and Azure DevOps.
* For SCM data migration, <code class="expression">space.vars.SITENAME</code> creates a virtual drive with latter on the machine where OpsHubTFSService is installed. OpsHubTFSService downloads the files from the source system that needs be checked in to the target Team Foundation Server (TFS) and Azure DevOps system. These downloaded files would be checked in by <code class="expression">space.vars.SITENAME</code> using the OpsHubTFSService to the target system.
