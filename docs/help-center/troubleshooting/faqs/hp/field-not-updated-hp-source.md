## Description

User has configured an integration from Micro Focus ALM/QC to any other system and user has followed the pre-requisites & best practices, but the target field value is not getting updated as per the updates done in the source system.

## Cause

In Micro Focus ALM/QC, **history** must be enabled for the fields that are used in the mapping. If history is not enabled, then it may lead to above-mentioned behavior.

>**Note**: To determine in which scenarios **history** must be enabled, please refer [Enable history of fields to be mapped](../../../connectors/micro-focus-alm-qc.md#enable-history-of-fields-to-be-mapped).

## Solution

* To enable history in Micro Focus ALM/QC, Please refer [How to enable history of fields to be mapped](../../../connectors/micro-focus-alm-qc.md#how-to-enable-history-of-fields-to-be-mapped).


