## Description

When you encounter error OH-Jama-0054, then following error message will appear:  
Error message: OH-Jama-0054: Link Type Test Group (or Test Plan) association is mandatory for Test Cycles.

## Cause

Probable cause for this issue is:  
When Jama system is target system and trying to create a link between Test Cycle and TestPlan if the required relationship mapping is not defined in OpsHub Integration Manager mapping section.

## Solution

- In OpsHub Integration Manager field mapping configuration, under the relationship configuration, please define relationship for ‘Test Plan’ with Test Cycle  
- Please refer to [**TestRail-Jama Integration**](testrail-jama-integration) for configuring links
