# Description
Null/Empty/Invalid values are coming for Mandatory fields in target system from the source system. How to prevent them?

# Solution

Mandatory fields for the target system are not mapped correctly. Please perform the following steps: 

* De-activate the integration. Open the mapping for which you received this error in the edit mode
* Map the Mandatory field with source system’s field or pass a default value by mapping the field with OH_Default
* Update the mapping, activate and save the integration again. Now, retry the failure

>**Note**: The best practice to avoid this failure is to make corresponding source field mandatory or always map it with a default field value during mapping.
