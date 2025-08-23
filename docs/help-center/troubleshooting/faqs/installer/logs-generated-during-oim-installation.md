## Description

Where to find the logs generated during {{SITENAME}} installation?

Logs generated during {{SITENAME}} installation are useful in identifying the reason for failure (if any).

## Solution

{{SITENAME}} installation progress gets logged in an `Install.log` file. It contains details of all the steps performed in the process, along with the details of failures (if any).  
This file is located under the 'logs' folder in {{SITENAME}} installation path.

For example:

Operating System: **Windows**  
Installation Path: `C:\Program Files\{{#ifeq: {{SITENAME}} | OpsHub Migrator for Microsoft Azure DevOps |OM4ADO|OpsHub}}`  
Location of log file: `C:\Program Files\{{#ifeq: {{SITENAME}} | OpsHub Migrator for Microsoft Azure DevOps |OM4ADO|OpsHub}}\logs\Install.log`

{{#ifeq: {{SITENAME}} | OpsHub Migrator for Microsoft Azure DevOps ||
Operating System: **Linux**  
Installation Path: `/usr/local/OpsHub`  
Location of log file: `/usr/local/OpsHub/logs/Install.log`
}}
