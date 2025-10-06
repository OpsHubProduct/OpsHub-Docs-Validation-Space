# Advance Mapping Utility

## Overview
* This Advance Utility is useful when user want some customization in default xslt or user have some specific requirement. For acheiving those requirement OpsHub Integration Manager provides some Utilities which handle some custom requirement.

## Common placeholder and its value

<p align="center">

| **Placeholder**   | **Value**                        | **Description** |
|:-----------------:|:--------------------------------:|-----------------|
| `<<Workflow Id>>`   | $workflowId                      | if workflowId is required for any utility pass it as $workflowId, it is always available in mapping xml. |
| `<<System Id>>`     | $sourceSystemId or $targetSystemId | If the requirement is to have the value for the source system then set this as '$sourceSystemId' and if the requirement is to have the value for the target system then set the value as '$targetSystemId'. |

</p>

## Utilities

### Get Field Value of Entity
* **Overview:** This Utility will help to fetch value of any field of specific entity.  
* **Utility Definition:**  
  ```code
  getEntityFieldValue(WorkflowId, SystemId, ProjectValue, EntityType, EntityId, FieldInternalName)
  ```
* This utility can be used in the advance xslt in this manner:  

  ```xml
  <xsl:value-of select="utils:getEntityFieldValue(<<Workflow Id>>,<<System Id>>,<<Project Value>>,<<Entity Internal Name>>,<<Entity Id>>,<<Internal Field Name>>)"/>
  ```
*How to set the placeholders:*  
- `<Workflow Id>`: refer [Common placeholder and its value](#common-placeholder-and-its-value) section.  
- `<System Id>`: refer [Common placeholder and its value](#common-placeholder-and-its-value) section.  
- `<Project Value>`: Pass project's value if required else pass null.  
- `<Entity Internal Name>`: Pass internal name for the entity.  
- `<Entity Id>`: Pass internal id of specific entity for fetching particular field's value.  
- `<Internal Field Name>`: Pass field's internal name for fetching value of it.  

---

### Get Matching Lookup Value of Target from Source

- **Overview:** This Utility will help to find matching lookup value from system by giving regular expression.  
- **Utility Definition:**  
  ```text
  getMatchingLookupValue(WorkflowId, SystemId, projectValue, EntityType, RegexExpression, isRegexOnInternalValue, isThrowErrorOnMultipleMatch, isRefreshOnCacheMiss)
  ```
* This utility can be used in advance xslt in this manner:  

```xml
<xsl:value-of select="utils:getMatchingLookupValue(<<Workflow Id>>,$targetSystemId,<<Project Value>>,<<Internal Field Name>>,<<RegexExpression>>,<<Regex on Internal Value>>,<<Throw Error On Multiple Match>>,<<Refresh On Cache Missing>>)"/>
```
*How to set the placeholders:*  
- `<<Workflow Id>>`: refer [Common placeholder and its value](#common-placeholder-and-its-value) section.  
- `<<Project Value>>`: Pass project's value if required else pass null.  
- `<<Internal Field Name>>`: Pass field's internal name for fetching value of it.  
- `<<RegexExpression>>`: Here, the user can pass a valid regular expression. If user wants to map the lookup values in such a way that it fetches the value which ends with field value of source entity, then pass `concat('.*','<<Searched value>>')`.  
- `<<Regex On Internal Value>>`: Pass this as `'true'`, if user wants to search value on basis of internal value of lookup, else pass `'false'` which will search on the basis of display value of lookup.  
- `<<Throw Error On Multiple Match>>`: Pass this as `'true'`, if user wants to throw error if multiple match are found for given expression, else pass `'false'` which will throw error in case there are multiple lookups with the same value found.  
- `<<Refresh On Cache Miss>>`: <code class="expression">space.vars.SITENAME</code> maintains cache for lookups to decrease the number of times API is called for the end system. If the user passes the value as `'true'`, {{SITENAME}} will reload the cache if a lookup with a certain value is not found. If this is passed as `'false'`, {{SITENAME}} will always refer the cache and will not reload the cache if a certain matching lookup is not found.  
