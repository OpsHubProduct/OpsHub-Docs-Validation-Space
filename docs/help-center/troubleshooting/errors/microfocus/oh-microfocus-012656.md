# Description

When user encounters OH-Micro Focus ALM/QC-012656, following error message will appear:

Micro Focus ALM/QC-012656: Test set folder cannot have duplicate name. Server error: Duplicate Test Set Folder: &lt;Exception Message&gt;

**Example:**  
Micro Focus ALM/QC-012656: Test set folder cannot have duplicate name. Server error: Duplicate Test Set Folder: 'A'  
OpsHub-012654: Error occurred in HPQC CRUD Request execution for operation createHpqcEntity.  
OH-Micro Focus ALM/QC-0055: Error encountered while creating new entity of type: test-set-folders

# Cause

* User will encounter this error in the following scenario:  
  * Entity with the same name that is already there within same parent.  
    **For example:**
    * The Root folder has three child Test Set folders named "Folder-1", "Folder-2", and "Folder-3". If you change "Folder-1" name to "Folder-2", then OpsHub Integration Manager gives the above mentioned error.
    * The Root folder has two child Test Set folders named "Folder-1", "Folder-2". Now if Test Set Folder getting synchronized is having name "Folder-1" then such processing failure can occur.

# Solution

User can apply a solution which results into unique Test Set folder names under same parent. Below are few examples for the same:

1. Create/Update entity in the source such that entity does not have duplicate name.
2. Update mapping such that unique name appears for synchronization. Refer to the following example for advance mapping:

## Update mapping such that Test Set Folder name = {name} + {source entity Id}. Below is a sample advance XML for mapping:

```xml
<Name xmlns:xsl="http://www.w3.org/1999/XSL/Transform">
  <xsl:value-of select="concat(SourceXML/updatedFields/Property/Name, ' [', SourceXML/opshubEntityId, ']')"/>
</Name>
```

If the source entity name is "QA folder" with internalId 22, it will create folder with name `QA folder [22]`.
