## Description

If a user has configured an integration between **Requirement** entity of Micro Focus ALM/QC and any entity of the target system and user has also configured the "Issue Relationship" to synchronize the Requirement Traceability, but the Requirement Traceability is not getting synchronized.

## Cause

A probable reason for this behavior could be a missing value of **Database Schema Name** and/or **Proxy URL** in the system configuration form for Micro Focus ALM/QC.

## Solution

* To synchronize the **Requirement Traceability** with Micro Focus ALM/QC, a user needs to mention **Database Schema Name** and/or **Proxy URL** in the system configuration form for specific versions of Micro Focus ALM/QC.
* To determine which particular field (Database Schema Name and/or Proxy URL) is required for a particular version of Micro Focus ALM/QC to synchronize Requirement Traceability, please refer [System configuration in Micro Focus ALM/QC](../../../connectors/micro-focus-alm-qc.md#system-configuration).

>**Note**: To configure proxy, please refer [Proxy Configuration](../../../connectors/micro-focus-alm-qc.md#proxy-configuration-steps).

>**Note**: To configure System, please refer [System Configuration](../../../integrate/system-configuration.md).

