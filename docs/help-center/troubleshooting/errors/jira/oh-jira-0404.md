## Description

When you encounter error OH-JIRA-0404, then following error message will appear:  
**OH-JIRA-0404**: Error occurred while requesting URL <<URL>>. Response received from server is Maximum results per request exceeded. Please paginate your request or contact you Jira Administrator. The current maximum is <<page size>>.

## Cause

* This error can be encounter when the user has configured the integration of the Jira[Xray] Test Execution entity and is trying to synchronize the Test linkage for the Test Execution.  
* This error is caused when the page size in the [Jira Xray settings](https://docs.getxray.app/display/XRAY/Miscellaneous#Miscellaneous-Maxresultsperrequest) is set to be less than 100.  
* As the API call to get Tests linked to a Test Execution is a paginated request, {{SITENAME}} expects the API page size in the URL to be at least 100.

## Solution

Please ensure that the page size in the [Jira Xray settings](https://docs.getxray.app/display/XRAY/Miscellaneous#Miscellaneous-Maxresultsperrequest) is 100 or more as {{SITENAME}} expects the page size to be at least 100.
