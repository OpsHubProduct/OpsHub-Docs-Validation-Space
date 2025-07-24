# Description

When the user encounters an error **OH-DOORS Next-0101**, then the following error message will appear:

**OH-DOORS Next-0101**: TARGET_LOOKUP Invalid: Missing field "`<Field Name>`" in Project "`<Project Name>`", Component "`<Component Name>`", Stream "`<Stream Name>`". Please check if there exists a case-sensitive field with name "`<Field Name>`" in Project "`<Project Name>`", Component "`<Component Name>`", Stream "`<Stream Name>`"

# Cause

When **Module Filter Query** setting is configured in integration for DOORS Next as source endpoint, and an error occurs for the field used in **Module Filter Query**, the cause is:  
**The field(s) used in **Module Filter Query** input does not exist as the field(s) in the end system for the artifact type for which integration is configured.**

# Solution

* Refer to the note(s) of the section [Synchronize artifacts from specific module(s)](../connectors/ibm-rational-doors-next-generation.md#synchronize-artifacts-from-specific-modules)
