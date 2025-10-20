## Description
When you encounter OH-JIRA-0174, then following error message will appear:

OH-JIRA-0174: For project <<Project Name>>, transition of issue to status <<State Which is going to be set in Jira>> is not available. The available transitions are: [<<Available Status1>>, <<Available Status2>>, <<Available Status3>>]

Example:  
OH-JIRA-0174: For project SampleProjectName, transition of issue to status Closed is not available. The available transitions are: [In Review, Accepted, Resolved]

## Cause
This error could come up when there is an issue with your Jira instance or <code class="expression">space.vars.SITENAME</code> mapping configuration. Refer [Need for handling workflow transition in Jira](../../../../connectors/jira.md#need-for-handling-workflow-transition) for understanding the cases in which this error can occur.

## Solution
Refer [Solution for handling workflow transition in Jira](../../../../connectors/jira.md#solution-for-handling-workflow-transition) for the resolution of this issue.

