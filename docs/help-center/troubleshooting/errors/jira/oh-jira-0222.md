## Description

When you encounter error OH-JIRA-0222, then following error message will appear:
An internal error occurred when getting the issue information. Server Error : 500 , response from server is :  
`<?xml version="1.0" encoding="UTF-8" standalone="yes"?><status><status-code>500<status-code><stack-trace>java.lang.NullPointerException ... </stack-trace></status>`

## Cause

If Jira contains SLAPowerbox plugin version 3.5.x, then it will throw the above-mentioned error.

## Solution

Please use OpsHub supported SLAPowerbox plugin version.

