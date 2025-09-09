## Description

When you encounter error OH-Jama-0102, then following error message will appear:  
OH-Jama-0102: Create entity failed as Component/Set/Folder field value is 'Component/Set/Folder field value' and container: 'Component/Set/Folder container name' is not found. Field checkAndCreate is disabled. Enable the same in mapping or configure appropriate Parent link in mapping instead of the field.

## Cause

Probable cause for this issue is:

- For any entity configured for synchronization other than Component/Set/Folder.  
- When the **Component/Set/Folder** field is mapped, and a value is coming in the field from the source system, then containers with these names are to be found and added to the aggregated location for the entity.  
- If the Component/Set/Folder value is not present and **checkAndCreate** is disabled, this error will be thrown.

>**Note**: By default, check and create of these relative location related fields is disabled in the field mapping.

## Solution

Mapping configuration needs to be updated in this case. Any one of the following configurations needs to be done:

- **Field configuration** – Advanced mapping can be done to enable `"checkAndCreate"` on the Component/Set/Folder field.  
  - An attribute named `"checkAndCreate"` needs to be added with value `"true"` in the XSL field tag.

  **Sample mapping:**
  ```xml
  <OH_FolderPath checkAndCreate="true">
    <xsl:value-of xmlns:xsl="http://www.w3.org/1999/XSL/Transform" select="SourceXML/updatedFields/Property/OH__FolderPath"/>
  </OH_FolderPath>
  ```
 