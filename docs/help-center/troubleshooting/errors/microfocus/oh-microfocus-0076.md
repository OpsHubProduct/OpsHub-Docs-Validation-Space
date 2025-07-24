# Description

When user encounters OH-Micro Focus ALM/QC-0076, then following error message will appear:

OH-Micro Focus ALM/QC-0076 : Error occurred while fetching list of projects therefore error in getting project metadata for system : &lt;SystemName&gt;.

# Cause

This error may occur while loading the list of projects in the following cases:

1. The username or the password used in Micro Focus system configuration is incorrect.  
2. The server URL used to connect to Micro Focus system is incorrect.

# Solution

* To check whether the username or password is correct or not, perform these steps:  
  * Try logging-in with the same username and password mentioned in the System Configuration form through the Micro Focus ALM/QC UI.  
  * If the login was not possible through Micro Focus ALM/QC UI, please check with your administrator for the correct credentials.

* To check whether the server URL mentioned in the System Configuration Form is correct or not, perform these steps:  
  * Try to access the Micro Focus ALM/QC UI in the browser using the server URL mentioned in the system configuration form.  
  * If Micro Focus ALM/QC UI is not accessible then, please contact your administrator.
