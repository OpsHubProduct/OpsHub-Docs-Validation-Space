 ## Description
When you encounter error OH-JIRA-0220, then following error message will appear:

OH-JIRA-0220: Error is due to: OH-JIRA-0219: Error occurred in Jira : {"errorMessages":["No Link Issue Permission for issue 'UA-2327'"],"errors":{}}. The issue is Link Issues permission is required on both the inward issue (linking to) and the outward issue (linking from) for linktype "blocks". Please check the "Link Issues" permission on both the source and target issues/projects.

## Cause
Probable causes for this issue are:
1. The user does not have the required **Link Issues** permission on the source issue (linking from).
2. The user does not have the required **Link Issues** permission on the target issue (linking to).
3. In some cases, the user may have the permission in one project but not the other, which still prevents linking.

## Solution
1. Verify that the user account being used has the **Link Issues** permission on both the source and the target issues/projects.
2. To check this:
   1. Go to the relevant projects in Jira.
   2. Navigate to *Project Settings > Permissions*.
   3. Ensure that the user (or the group/role the user belongs to) has the **Link Issues** permission in both projects.
3. If the permission is missing, request your Jira administrator to update the permission scheme and grant the **Link Issues** permission.
