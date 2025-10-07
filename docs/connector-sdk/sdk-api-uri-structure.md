# URI Structure for the APIs

The URI structure for the APIs should follow this format:  
https://{host}:{port}/.../.../{sdk-version}/{resource-name}


- The user can decide the URI structure before `{sdk-version}` and keep it as per their requirement.  
- SDK **version** should be **1.0** as of now. In the future, if <code class="expression">space.vars.SITENAME</code> wants to extend APIs for any major change, the version may change to **2.0** to provide backward compatibility.  
- **resource-name**: All the APIs are categorized into resources. For example: Configuration, Entities, Users, Attachments, etc.
