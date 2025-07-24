# Description

When user encounters OH-Micro Focus ALM/QC-012612, then following error message will appear:

'OH-Micro Focus ALM/QC-012612 : Error in response from Quality Center, because of: Exception Code From QC - &lt;Exception from QC&gt : Exception Message - &lt;Exception Message&gt;'

# Cause

This error may occur when an integration is configured for any source system to Micro Focus ALM\QC and OpsHub Integration Manager is trying to make a request to the Micro Focus ALM/QC server, but the Micro Focus ALM/QC server can not process due to following reasons.

* The exception from QC - **qccore.invalid-list-field-value** could occur when invalid value is given for the lookup type of field.
* The exception from QC - **qccore.required-field-missing** could occur when value is not assigned/set for the mandatory field.
* The exception from QC - **qccore.invalid-value-type-for-field** could occur in following possible scenarios.
  * Text type of field is mapped to Date type of field in the mapping configuration.
  * Text type of field is mapped to Time type of field in the mapping configuration.
  * Text type of field is mapped to Number type of field in the mapping configuration.

# Solution

* If exception from QC is **qccore.invalid-list-field-value**, then please check the advanced mapping configuration for the field specified in the exception Message. In the advanced XSLT, please make sure that all the values assigned for the lookup type of field are valid.
* If exception from QC is **qccore.required-field-missing**, then please make sure that the source field which is mapped to the mandatory field specified in the exception message is assigned some value.
  * One can also use default value mapping for the mandatory field. To set default value, please refer [default value mapping](../integrate/mapping-configuration#default-mapping)
* If exception from QC is **qccore.invalid-value-type-for-field**, then please check the mapping configuration for the field specified in the exception Message.
  * If the Text type of field is mapped to the Date/ Time/ Number type of field, then it is an invalid type of mapping, such field mappings shall be avoided. For that, user needs to remove such invalid field mappings and configure valid field mapping based on data-type combination.
  * If user still intends to use such kind of mappings, then the field in the source system must be assigned the value that will be compatible with the type of the target field.
