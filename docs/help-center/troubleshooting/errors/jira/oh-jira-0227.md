## Description

When you encounter error OH-JIRA-0227, then following error message will appear:

 **OH-JIRA-0227**: Unexpected response received from JIRA. Please check whether user has sufficient permissions and whether user has access to JIRA Software. Refer Jira prerequisites in the {{SITENAME}} documentation.

## Cause

If user is getting this error code then it might be because the sync user that is used in the Jira system configuration doesn't have access to Jira license.

## Solution

For solving this issue, please check if the sync user has been given access for the necessary applications used in the Jira system configuration. For more information on the required application access, refer:  
[License required by sync user in Jira](../../../../connectors/jira.md#licenses-required)

