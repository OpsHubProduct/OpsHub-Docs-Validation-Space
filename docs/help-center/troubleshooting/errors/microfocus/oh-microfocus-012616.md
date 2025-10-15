# Description

When user encounters OH-Micro Focus ALM/QC-012656, following error message will appear:

'Micro Focus ALM/QC-012616: Rest request processing Error : 500 Server Error : Probable cause for this error can be either the password entered in the System configuration form is wrong or the server has encountered the condition, which cannot process your request `<request URL>` (Please check the logs for the detailed response from server). OpsHub-012654: Error Occurred in HPQC CRUD Request execution for operation getMaxUpdateTime `<Server Response Stack Trace>` org.hp.qc.api.entities.InvalidValueForFieldException: Failed to convert the 'time' field of a 'audit-log'. The object 2000-01-01+00:00:00 cannot be converted to type QcDate&#xD'

# Cause

* User will encounter this error in the following scenario:  
  * When the user is running integration(s) of release-cycle in <code class="expression">space.vars.SITENAME</code> having version 7.141 or above **and** your legacy Micro Focus application only accepts '%20' as the encoding of the ' ' (space character) in its API.

# Solution

* Open the directory where <code class="expression">space.vars.SITENAME</code> is installed and navigate to `OpsHub_Resources/config` directory.
* **Duplicate** the `HPQCProperty.properties.sample` file and **rename** it to `HPQCProperty.properties`.
* Now set the `hpQueryParamEncoding` flag to `true` and restart the OpsHub server service.
