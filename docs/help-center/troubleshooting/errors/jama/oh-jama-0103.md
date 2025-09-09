### Description

When you encounter error OH-Jama-0103, then following error message will appear:  
> OH-Jama-0103: Error occurred while updating entity in Jama. Child Item Type field can't be updated.

### Cause

Probable cause for this issue is:

- For creating a Set in Jama, **Child Item Type** field must be present.  
- Once a Set gets created in Jama with a specific Child Item Type, the child item type can't be modified through the Jama API.  
- With respect to the above end system behavior, when any update comes on **Set** entity field **Child Item Type**, OpsHub Integration Manager will raise this error.

### Solution

Set **"Sync When?"** settings for the **"Child Item Type"** field to **"Create"**:

- Set the **"Child Item Type"** field to be mapped for the **Create** event only.  
- To do this, skip update synchronization on the **"Child Item Type"** field by selecting the **"Create"** option under the **"Sync When?"** setting in the field mapping.  
- For more information on the **"Sync When?"** setting, refer to the document [**Advance Settings Sync When?**](../../../../integrate/mapping-configuration.md#sync-when)
