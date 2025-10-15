# oh-microfocus-012652

## Description

When user encounters OH-Micro Focus ALM/QC-012652, then following error message will appear:

'OH-Micro Focus ALM/QC-012652 : Invalid Field name used in the mapping therefore error in response from Quality Center, because of: `<Exception from QC>` : Exception Message - `<Exception Message>`.

**Example:**\
OH-Micro Focus ALM/QC-012652 : Invalid Field name used in the mapping therefore error in response from Quality Center, because of: qccore.unknown-field-name : Exception Message - Entity: requirement doesn't have a field named: 'user-xx'

## Cause

* User might encounter this error in the following scenarios:
  * When a custom field that is used in mapping is available on Micro Focus ALM/QC UI as well as in <code class="expression">space.vars.SITENAME</code> mapping configuration, but it is not associated with the Requirement Type entity that is used in integration.\
    &#xNAN;_**For example**_, the custom field `user-xx` is available on Micro Focus ALM/QC UI as well as in <code class="expression">space.vars.SITENAME</code> mapping configuration, but it is not associated with Requirement type entity that is used in the integration. Also, the user has used the custom field `user-xx` in the mapping between Requirement of Micro Focus ALM/QC and any other system.
  * When in an integration configured with criteria, the internal name for the field mentioned in the criteria query is incorrect.

## Solution

* To associate any custom field with the requirement type that is being used in integration, please refer\
  [How to associate a custom field with the Requirement](../../../../connectors/micro-focus-alm-qc.md#how-to-associate-a-custom-field-with-requirement)
* To determine the internal name for the criteria configuration please refer\
  [How to find the internal name](../../../../connectors/micro-focus-alm-qc.md#how-to-find-out-internal-name2fkey-in-versions)
