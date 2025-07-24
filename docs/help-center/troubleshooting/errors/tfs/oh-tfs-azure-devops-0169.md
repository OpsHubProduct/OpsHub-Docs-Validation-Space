## Description

When you encounter OH-TFS/Azure DevOps-0169 then the following error messages will appear:

"OH-TFS/Azure DevOps-0169: Create or Update entity of type `<Entity_Type>` for `<Project_Name>` project is failing. Error received from the server: Failed to create/update entity because : InvalidEmpty for field [`<Field>`] value [`<Value>`]".

## Cause

Following are the probable reasons for this:
* Mandatory fields have not been configured while doing field configuration.
* Invalid value is being written in `<Field>`, which is not acceptable by Team Foundation Server (TFS)/Azure DevOps. 

## Solution

* You need to configure all the fields which are mandatory from Team Foundation Server (TFS)/Azure DevOps Interface while configuring mapping for integration. 
* In case you have mapped non-mandatory source field with Mandatory target field, then you can provide [Default Mapping](../../integrate/mapping-configuration.md#default-mapping) for that field.
* If any rule is configured in Team Foundation Server (TFS)/Azure DevOps interface that prevents invalid values to be written in the fields then you need to do field mapping accordingly. Here also you can provide [Default Mapping](../../integrate/mapping-configuration.md#default-mapping) for the field for which error is coming.
