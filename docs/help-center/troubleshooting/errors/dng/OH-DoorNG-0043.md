# Description

When you encounter an error **OH-DOORS Next-0043**, then the following error message will appear:

**OH-DOORS Next-0043**: The module of an artifact cannot be changed. Hence, map the "Module" field only for create. We need to skip this field synchronization when the entity getting updated. To skip this field synchronization set the "Create" option under "Sync When?" settings in the field mapping.    

# Cause

* This error will come when DOORS Next is the target end system and the "Module" field is mapped.
* Module of an artifact can't be changed in the end system once the artifact is created in the module.
* Thus whenever an update comes on an entity with "Module" field change, then an error will encounter.
* This behavior corresponds to the DOORS Next end-system behavior i.e.  
**once a shared artifact is created i.e artifact created under the module then the module of an artifact cannot be changed**

# Solution

* The **"Module"** field must be mapped for **Create** event only.
* For doing this configuration, skip the **"Module"** field synchronization by setting **"Create"** option under **"Sync When?"** settings in the field mapping.
* For information on **"Sync When?"** setting, refer to document [Advance Settings Sync When?](../../../../integrate/mapping-configuration.md#sync-when)
