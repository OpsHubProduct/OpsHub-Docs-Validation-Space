## Description

This behavior is applicable when any update done on ServiceNow entities are not getting synchronized to the other end system.

## Cause

The possible reason could be: Audit is not enabled for the entities that are being synchronized.

## Solution

ServiceNow tracks incident, change, and problem history in the `sys_audit` table.  
Enabling auditing tracks the creation and update of audited records.  

Audit must be enabled on the entity table (not on its import set table, but on the actual entity table like `incident`, `problem`, etc.).  

To enable audit for a table, please refer [Enabling audit for a table](../../../connectors/servicenow.md#turn-on-auditing-history-for-a-table).


