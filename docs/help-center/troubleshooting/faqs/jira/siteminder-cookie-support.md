## Description
Does Cookie-based Authentication feature for Jira work with a SiteMinder cookie/any third-party cookie?

## Solution
Siteminder cookie is not supported by {{SITENAME}}.  
{{SITENAME}} works on Jira's internal cookie management and sends the username and password to Jira, and Jira, in turn, shares the cookie that needs to be used for the subsequent request.

This facilitates one-time login in Jira for every API call made rather than multiple logins in Jira for each API call made.  

For more information on the types of authentication that is supported in On-Premise Jira, refer: [Which authentication modes for Jira Server are supported by {{SITENAME}}?](Which_authentication_modes_for_Jira_Server_are_supported_by_LOCAL_TEST_MEDIAWIKI.md)
