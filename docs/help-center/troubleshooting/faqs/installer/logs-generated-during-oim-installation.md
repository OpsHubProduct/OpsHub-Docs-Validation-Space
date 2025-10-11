## Description

Where to find the logs generated during <code class="expression">space.vars.SITENAME</code> installation?

Logs generated during <code class="expression">space.vars.SITENAME</code> installation are useful in identifying the reason for failure (if any).

## Solution

<code class="expression">space.vars.SITENAME</code> installation progress gets logged in an `Install.log` file. It contains details of all the steps performed in the process, along with the details of failures (if any).  
This file is located under the 'logs' folder in <code class="expression">space.vars.SITENAME</code> installation path.

For example:

Operating System: **Windows**  
Installation Path: `C:\Program Files\{% if "OpsHub Migrator for Microsoft Azure DevOps" === space.vars.SITENAME %}OM4ADO{% endif %}{% if "OpsHub Integration Manager" === space.vars.SITENAME %}OpsHub{% endif %}`  
Location of log file: `C:\Program Files\{{#ifeq: <code class="expression">space.vars.SITENAME</code> | OpsHub Migrator for Microsoft Azure DevOps |OM4ADO|OpsHub}}\logs\Install.log`

{{#ifeq: <code class="expression">space.vars.SITENAME</code> | OpsHub Migrator for Microsoft Azure DevOps ||
Operating System: **Linux**  
Installation Path: `/usr/local/OpsHub`  
Location of log file: `/usr/local/OpsHub/logs/Install.log`
}}
