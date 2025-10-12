## Description

For integration from Micro Focus ALM/QC to any other target system, if Comments synchronization is enabled, the new comments [Added with 'Add Comment'] on Micro Focus ALM/QC entity will be synchronized/added to a target system. But if an already added comment is edited in Micro Focus ALM/QC, then it will be added as a new comment in the target system.

## Cause

In Micro Focus ALM/QC, for the comment field, if the user made an update to an already added comments then the revision about this updation is not maintained. The entire text present in the comment field of the entity of Micro Focus ALM/QC gets synchronized to the target system.

## Solution

When the comments are mapped from Micro Focus ALM/QC to any target system and the user updates the comment in Micro Focus ALM/QC for the synchronized entity, then to know the behavior for updating the comment in the target, please refer [Micro Focus ALM/QC Comments](../../../connectors/micro-focus-alm-qc.md#micro-focus-alm-comments).


>**Note**: To know how to map comments in <code class="expression">space.vars.SITENAME</code>, please refer mapping [Comments](../../../integrate/mapping-configuration.md#comments) in the documentation.

