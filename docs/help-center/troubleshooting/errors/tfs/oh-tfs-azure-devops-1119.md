## Description

When you encounter error OH-TFS/AzureDevOps-1119 then the following error message will appear:

'OH-TFS/AzureDevOps-1119:Error occurred while creating/updating a dashboard. You can either give Owner field value or Owned by team field value for creating a dashboard. Please update the mapping configured. Owner value is <owner name> and Owned by team value is `<team name>`'

## Cause

Following is the reason for this:

1. In Team Foundation Server/Azure DevOps, a **Dashboard** can be created with **Dashboard Type** as **Project Dashboard** or a **Team Dashboard**.
   * For creating a Team Dashboard, **Owned by team** field is used and for creating a **Project Dashboard**, **Owner** field is used.
   * If both the fields are passed during create and both have some values, then <code class="expression">space.vars.SITENAME</code> is unable to identify whether a **Project Dashboard** needs to be created or a **Team Dashboard** needs to be created.
   * In this case, <code class="expression">space.vars.SITENAME</code> throws this error.

## Solution

* You need to make sure that the source system is sending value in any one of the **Owner** and **Owned by team** fields.
* You can configure the field mapping such that, **Owned by team** field is set when **Team Dashboard** needs to be created and **Owner** field is set when **Project Dashboard** needs to be created in target end system.
