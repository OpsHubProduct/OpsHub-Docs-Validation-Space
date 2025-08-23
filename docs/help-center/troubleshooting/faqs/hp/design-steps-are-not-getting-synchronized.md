## Description

The user has configured an integration between **Test Plan** entity of Micro Focus ALM/QC and any entity of the target system. The field **Design Steps** of the Test Plan entity has been mapped to the relevant field entity in the target system; however, they aren't getting synchronized.

## Cause

A probable reason for this behavior can be a missing value of **Database Schema Name** and/or **Proxy URL** in the system configuration form for Micro Focus ALM/QC.

## Solution

* To synchronize the **Design Steps** with Micro Focus ALM/QC, a user needs to mention **Database Schema Name** and/or **Proxy URL** in the system configuration form for specific versions of Micro Focus ALM/QC.  
* To determine which particular field (Database Schema Name and/or Proxy URL) is required for a particular version of Micro Focus ALM/QC to synchronize Requirement Traceability, please refer [System configuration in Micro Focus ALM/QC](../../../../connectors/micro-focus-alm-qc.md#system-configuration).

>**Note**: To configure proxy, please refer [Proxy Configuration](../../../../connectors/micro-focus-alm-qc.md#proxy-configuration-steps).

>**Note**: To configure System, please refer [System Configuration](../../../../integrate/system-configuration.md).
design-steps-are-not-getting-synchronized
