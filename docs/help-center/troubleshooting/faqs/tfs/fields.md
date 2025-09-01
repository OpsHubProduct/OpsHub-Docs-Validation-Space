## Description

Team Foundation Server (TFS)/Azure DevOps fields contain Read-Only fields and Writable fields. Not all of these fields are supported for synchronization.

## Solution

* All the fields that are writeable from the User Interface can also be writeable from {{SITENAME}}. It can be an HTML, Text, User, Numeric, Boolean, or Lookup field.
* Few fields such as ID, Watermark, etc. are Read-Only fields. These fields cannot be writeable but their field values can be readable by {{SITENAME}}. Refer [Team Foundation Server - Common](../../../connectors/team-foundation-server.md#known-behaviors-and-limitations) section's step 3 to get list of Read-Only fields.  
{{#ifeq: {{SITENAME}} | OpsHub Migrator for Microsoft Azure DevOps || * In Team Foundation Server (TFS)/Azure DevOps, there are fields such as Changed By, Changed Date for which auto-generated values can be overwritten. For this, By-Pass Rule should be enabled during system configuration. Refer table under [Team Foundation Server - Common](../../../connectors/team-foundation-server.md#known-behaviors-and-limitations) section to check which all fields are supported with and without By-Pass with different API option.}}


