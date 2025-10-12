## Description
Which authentication modes for Jira On-Premise instance are supported for synchronization?

## Solution
There are two types of authentication modes that are supported for Jira On-Premise instance. In both of these authentication modes username and password of the user will be used but <code class="expression">space.vars.SITENAME</code> will internally handle how it will make authenticated REST API request with the server.

These are the two authentication modes:
1. **Basic Authentication**: If this mode is selected, then Jira will internally log-in for every API call sent during integration. 
2. **Cookie-based Authentication**: If this mode is selected, then one-time cookie session will be generated that will be used for all subsequent API requests sent during integration.

It is recommended to use Jira Cookie-based Authentication over Basic Authentication as there would be significant improvement in <code class="expression">space.vars.SITENAME</code>'s performance as Jira will not login for every API call sent during integration.

**<code class="expression">space.vars.SITENAME</code> support for Cookie-based Authentication:**  
The Cookie-based Authentication for Jira system has been incorporated from <code class="expression">space.vars.SITENAME</code> Version 6.9 U1.

**How to Configure**  
Configure Authentication Type in system configuration of Jira. For more details on Jira's system configuration refer: [System Configuration of Jira](../../../connectors/jira.md#system-configuration)


