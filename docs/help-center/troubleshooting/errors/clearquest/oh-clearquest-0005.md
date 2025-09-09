## Description

When the user encounters OH-ClearQuest-0005, the following error message will appear:

Example: 
:: OH-ClearQuest-0005: Proxy Error : Error occurred while creating record in ClearQuest, because of OH-ClearQuest-0005: Proxy Error : Error occurred while creating record in ClearQuest, because of CRVAP0065E Not all properties were successfully updated.  
CRVAP0226E Internal error: Status 500; Condition null; Message: CRVSV0078E Error from RPC server: CRVSV0768E Could not update property: CRMCU0018E Failed condition: AdIsNonEmpty(value)  
Location: ClearQuest Core:adfield.cpp:852  
CRVAP0226E Internal error: Status 500; Condition null; Message: CRVSV0078E Error from RPC server: CRVSV0768E Could not update property: CRMCU0018E Failed condition: AdIsNonEmpty(value)  
Location: ClearQuest Core:adfield.cpp:852

## Cause

*This issue occurs due to the requirement of IBM Rational ClearQuest API for the multi-select field, which is mapped.*

## Solution

Update the field properties as mentioned in the [Multi-Select Type Fields](../../../../connectors/ibm-rational-clearquest.md#multi-select-type-fields) section in IBM ClearQuest Rational connector documentation.
