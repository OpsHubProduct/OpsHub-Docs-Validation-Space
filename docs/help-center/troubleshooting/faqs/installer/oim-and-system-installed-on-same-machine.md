## Description

Can {{SITENAME}} and an end system that is being used in integration be installed on the same machine? For example: If an integration is created between System A and System B, then A and B are the end systems. If the {{SITENAME}} is installed on the same machine where System A or System B is hosted then same machine is being used for end system and application.

## Solution

{{SITENAME}} can be installed on the same machine where one of the end system is installed. However, the machine on which OpsHub Integration Manager is being installed must fulfill the [Installation Prerequisites](../../../getting-started/prerequisites.md#installation-prerequisites). It is preferable to have separate VM's for both, as the system may take up more resources if the number of users accessing it increases. In such scenario, it would be necessary to ensure that {{SITENAME}} gets its required share of resources or it will affect the performance of {{SITENAME}}


