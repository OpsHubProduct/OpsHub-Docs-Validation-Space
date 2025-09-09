## Description
When you encounter OH-JIRA-0173, then following error message will appear:

OH-JIRA-0173: Error occurred with status code: <status code> in JIRA. Reason: `<Reason from Jira Server>`

Example:  
OH-JIRA-0173: Error occurred with status code: 400 in JIRA. Reason: {"errorMessages":["Error in the JQL Query: Expecting operator but got 'and'. The valid operators are '=', '!=', '<', '>', '<=', '>=', '~', '!~', 'IN', 'NOT IN', 'IS' and 'IS NOT'. (line 1, character 72)"],"errors":{}} OpsHub-011257: Error occurred in getting issues from JIRA query: "updated >= "2019-8-22 7:44" and updated <= "2019-8-22 19:45" and wrong and project = "SampleProject" and issuetype = "10004""

## Cause
There can be various reasons for this error. Please refer `'''<status code>'''` and '''Reason: `<Reason from Jira Server>`''' part of the error message for finding the actual cause. This '''<status code>''' and '''Reason: <Reason from Jira Server>''' is part of the response that is coming from the Jira's REST API request made from {{SITENAME}}.

## Solution
Please check the '''Reason: <Reason from Jira Server>''' part of the error message. Search this reason in API Documentation/FAQs/Community/Support in Atlassian Jira to know when and why users can get this error from Jira. One of the reasons that users might be getting this error is something might be wrong with the {{SITENAME}}'s system, mapping or integration configuration. So, if the reason for the error is because of some configuration issue, change the configuration accordingly and retry the failure again. For knowing more about retrying the failure, refer: [Event Failure Management Overview in Manage Integration Failures](../../../manage-integration-failures.md#event-failure-management-overview)

For example, if you encounter the below error, then change the value of "Xray plugin version" field of Jira configuration form with your existing installed Xray plugin version.
  
OH-JIRA-0173: Error occurred with status code: 400 in JIRA. Reason: {"errorMessages":["We can't create this issue for you right now, it could be due to unsupported content you've entered into one or more of the issue fields. If this situation persists, contact your administrator as they'll be able to access more specific information in the log file.]}
