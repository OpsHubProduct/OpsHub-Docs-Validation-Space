## Description

When the user encounters OH-Jama-0046, then the following error message will appear:  
"OH-Jama-0046: You must set the following required fields. fields: attachment"

## Cause

There is Jama API limitation that if Read-Only check for Attachment Itemtype is not enabled, then attachments cannot be uploaded via API and so synchronization of attachments via OIM will not be possible.

## Solution

[**Jama Attachment Configuration**](../../../../connectors/jama.md#attachment_configuration)
