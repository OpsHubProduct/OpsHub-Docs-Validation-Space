## Description

When you encounter error OH-Jama-0069, then following error message will appear:  
OH-Jama-0069: Error occurred while creating entity in Jama.

## Cause

Probable cause for this issue is:  
When the mandatory fields for Jama are not mapped in the field mappings, <code class="expression">space.vars.SITENAME</code> will raise this error.

## Solution

All the mandatory fields in JAMA should be mapped or be provided a default value.
