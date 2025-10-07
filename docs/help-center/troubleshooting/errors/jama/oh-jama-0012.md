## Description

When you encounter error OH-Jama-0012, then following error message will appear:  
**OH-Jama-0012:** Error occurred while parsing the given datetime string `<actual date>`, as it is not in the expected format: `<expected format>`

## Cause

Probable causes for this issue are:

- Date format can be configured in Jama self-hosted instance at instance level and same format information needs to be added in system configuration in <code class="expression">space.vars.SITENAME</code>.
- If the date format details are not same as configured in Jama and provided in <code class="expression">space.vars.SITENAME</code> then <code class="expression">space.vars.SITENAME</code> will raise the above error.

## Solution

In <code class="expression">space.vars.SITENAME</code>, for Jama system configuration, provide the correct date format as its configured in Jama end system.
