## Description

When you encounter error OH-Jama-0100, then following error message will appear:  
OH-Jama-0100: Error occurred while creating Folder entity in Jama. Either ''Location''/''Location Path'' field or ''Parent'' Link must be mapped in mapping for creating a Folder.

## Cause

Probable cause for this issue is:

- Jama allows Folder creation inside a specific Set or a Folder, i.e. a Folder can only be created under a Set or another Folder.  
- In <code class="expression">space.vars.SITENAME</code>, the parent location can be provided using the field **Location/Location Path** or using link type **Parent**.  
- Thus, when folder entity synchronization is going on and the parent location is neither configured using field nor using link, then the create will fail.

## Solution

Mapping configuration needs to be updated in this case. Any one of the following configuration needs to be done:

- **Field configuration** – Location or Location Path needs to be mapped in field mapping.  
- **Link configuration** – Parent link needs to be configured for Set in the relationship mapping.
