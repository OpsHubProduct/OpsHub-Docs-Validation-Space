## Description

When you encounter an error **OH-DOORS Next-0045**, then the following error message will appear:

**OH-DOORS Next-0045**: Field "In Folder" cannot be changed for the artifact created under the module. This field belongs to the core artifact on the end-system and not to the shared artifact. This error can be resolved by doing mapping change 1) Either by setting a "Sync When?" setting to "Create" for this field or 2) Configure an advance mapping to allow an update when the artifact being updated is not a module artifact. Refer to the OIM product guide for more details over an error and resolution.

## Cause

* This error will come only when DOORS Next is the target end system and both the "In Folder" and "Module" field is mapped.
* **DOORS Next end-system behavior**  
  * When an artifact is created into a module, there are two artifacts created. One is a [base or core artifact](../../../../connectors/ibm-rational-doors-next-generation.md#glossary) - created inside the module's asset folder and the other one is a [shared artifact](../../../../connectors/ibm-rational-doors-next-generation.md#glossary) - created inside the module.
* **OpsHub Integration Manager behavior**  
  * As the **"In Folder"** corresponds to a field of base artifact (the artifact created in module's asset folder). Hence in OIM, this field gets used to create base artifact when artifact in sync is shared artifact.  
  * Thus, once an artifact is created in a module, the base artifact's folder can't be updated with a further update on module artifact as this field belongs to the base artifact, not to the shared artifact.

## Solution

There are two solutions to this problem:

### Option 1: Set "Sync When?" Settings for "In Folder" field to "Create"

* Set the **"In Folder"** field to be mapped for Create event only.
* For doing this configuration, skip the **"In Folder"** field synchronization by setting **"Create"** option under **"Sync When?"** settings in the field mapping.
* For information on **"Sync When?"** setting, refer to document [Advance Settings Sync When?](../../../../integrate/mapping-configuration.md#sync-when)

> **Note**: As doing this setting synchronizes In Folder field for Create events only, make sure you use this mapping for shared artifacts synchronization and a separate mapping for core artifacts synchronization if you want to sync In Folder Field for All(Create and update) events. In case you want to use the same mapping for both shared and base artifacts then you can use Option 2.

### Option 2: Configure an advance mapping to allow folder update only when a [base artifact](../../../../connectors/ibm-rational-doors-next-generation.md#glossary) is getting updated and not a [shared artifact](../../../../connectors/ibm-rational-doors-next-generation.md#glossary)

We want to update the folder field only for a base artifact. Thus, we need to determine whether the target artifact getting updated is a base artifact or a shared artifact. This information can be derived based on your environment/configuration.

Given below are few of the examples for deriving whether the artifact is a base artifact or a shared artifact. In the below mappings, we are checking the [Module](../../../../connectors/ibm-rational-doors-next-generation.md#fields-available-in-doors-ng) field of the target artifact to reach to the conclusion of its type. If Module field is empty, then it's considered as a base artifact and if a value is found, then it's considered as a shared artifact.

#### Example 1:

This mapping can be used when the artifact in DOORS Next target system has id of source entity in any field (Here the field is Launch URL). It takes an [OpsHub query](../../../../integrate/opshub-query-format.md#query-structure) and execute the utility method `getEntityFieldValueByQuery` to know whether the target artifact is present in the given Module or not. Based on this information, the folder update is allowed only when base artifact is getting updated.

The OpsHub query used in the sample mapping is  
```json
{"condition":"and","criterias":[{"field":"Launch URL","condition":"=","value":"<Source entity id>"},{"field":"Module","condition":"=","value":"<Module name>"}]}
```

```xml
<xsl:if test="true()" xmlns:xsl="http://www.w3.org/1999/XSL/Transform">
    <xsl:variable name="targetProjectId" select="'_2VRksvG2EeqPKMEVY9xANg:::_Ss6VYB25EeuQ3q-hiHNzSg:::_StDfVh25EeuQ3q-hiHNzSg'" />
    <xsl:variable name="sourceEntityId" select="SourceXML/opshubEntityId" />
    <xsl:variable name="targetModuleScope" select="'Target Module'" />
    <xsl:variable name="queryToExecute" select="concat('{&quot;condition&quot;:&quot;and&quot;,&quot;criterias&quot;:[{&quot;field&quot;:&quot;Launch URL&quot;,&quot;condition&quot;:&quot;=&quot;,&quot;value&quot;:&quot;',$sourceEntityId,'&quot;},{&quot;field&quot;:&quot;Module&quot;,&quot;condition&quot;:&quot;=&quot;,&quot;value&quot;:&quot;',$targetModuleScope,'&quot;}]}')" />
    <xsl:variable name="moduleOfTargetEntity" select="utils:getEntityFieldValueByQuery($workflowId,$targetSystemId,$targetProjectId,'Requirement(Text)',$queryToExecute,'oh_module')" />
    <xsl:choose>
        <xsl:when test="$moduleOfTargetEntity=''">
            <oh_in_folder xmlns:xsl="http://www.w3.org/1999/XSL/Transform">
                <xsl:value-of select="SourceXML/updatedFields/Property/oh__in__folder"/>
            </oh_in_folder>
        </xsl:when>
    </xsl:choose>
</xsl:if>
```

> **Note**: For this mapping to work, the source entity id must be present in a single target artifact. If a single or multiple artifacts are found having same source entity id, then the OpsHub Integration Manager will consider the first result and the mapping will not allow update for the folder field. If no artifacts are found, then the mapping will allow update for the folder field.

#### Example 2:

This mapping can be used when the entity in source system has remote link of target artifact in any field (Here the field is Remote Entity URL). It extracts the target artifact id from remote link (present in source entity) and execute the utility method `getEntityFieldValue` to know whether the target artifact is present in the given Module or not. Based on this information, the folder update is allowed only when the artifact is a base artifact.

```xml
<xsl:if test="true()" xmlns:xsl="http://www.w3.org/1999/XSL/Transform">
    <xsl:variable name="targetProjectId" select="'_2VRksvG2EeqPKMEVY9xANg:::_Ss6VYB25EeuQ3q-hiHNzSg:::_StDfVh25EeuQ3q-hiHNzSg'" />
    <xsl:variable name="remoteLinkInSourceEntity" select="SourceXML/updatedFields/Property/Remote-space-Entity-space-URL" />
    <xsl:variable name="resourceURLPrefix" select="'/resources/'"/>
    <xsl:variable name="resourceURLSuffix" select="'&vvc.configuration'"/>
    <xsl:variable name="targetEntityId" select="substring-after(substring-before($remoteLinkInSourceEntity,$resourceURLSuffix),$resourceURLPrefix)"/>
    <xsl:variable name="moduleOfTargetEntity" select="utils:getEntityFieldValue($workflowId,$targetSystemId,$targetProjectId,$targetEntityId,'oh_module')" />
    <xsl:choose>
        <xsl:when test="$moduleOfTargetEntity=''">
            <oh_in_folder xmlns:xsl="http://www.w3.org/1999/XSL/Transform">
                <xsl:value-of select="SourceXML/updatedFields/Property/oh__in__folder"/>
            </oh_in_folder>
        </xsl:when>
    </xsl:choose>
</xsl:if>
```
