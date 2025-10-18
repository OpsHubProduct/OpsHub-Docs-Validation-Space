## Description

Where to find the logs generated during <code class="expression">space.vars.SITENAME</code> installation?

Logs generated during <code class="expression">space.vars.SITENAME</code> installation are useful in identifying the reason for failure (if any).

## Solution

<code class="expression">space.vars.SITENAME</code> installation progress gets logged in an `Install.log` file. It contains details of all the steps performed in the process, along with the details of failures (if any).  
This file is located under the 'logs' folder in <code class="expression">space.vars.SITENAME</code> installation path.

For example:

Operating System: **Windows**  
{% if "OpsHub Migrator for Microsoft Azure DevOps" === space.vars.SITENAME %}  
Installation Path: `C:\Program Files\OM4ADO`  
Location of log file: `C:\Program Files\OM4ADO\logs\Install.log`
{% endif %}
{% if "OpsHub Integration Manager" === space.vars.SITENAME %}  
Installation Path: `C:\Program Files\OpsHub`  
Location of log file: `C:\Program Files\OpsHub\logs\Install.log`  

Operating System: **Linux**  
Installation Path: `/usr/local/OpsHub`  
Location of log file: `/usr/local/OpsHub/logs/Install.log`  
{% endif %}
