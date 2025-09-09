# Description

When user encounters **OH-Micro Focus ALM/QC-0078**, then following error message will appear:

'OH-Micro Focus ALM/QC-0078 : Error occurred while processing the request `<request URL>`, please re-check the username and password entered on system configuration form'.

# Cause

This error may occur in the following cases:

1. The username or the password used in Micro Focus system configuration is incorrect.  
2. The user specified in the Micro Focus system configuration is inactive.

# Solution

- To check whether the username or password is correct or not, perform these steps:  
  - Try logging-in with the same username and password mentioned in the System Configuration form through the Micro Focus ALM/QC UI.  
  - If the login was not possible through Micro Focus ALM/QC UI, please check with your administrator for the correct credentials.  

- If Username and Password combination is correct and you are still getting this error, then check that the user mentioned in the System Configuration form is an active site user in Micro Focus ALM/QC.  
  - To make the user as an **Active Site User**, please refer to [Activate the Site User](../../../../connectors/micro-focus-alm-qc.md#activate-the-user-as-a-site-user).

