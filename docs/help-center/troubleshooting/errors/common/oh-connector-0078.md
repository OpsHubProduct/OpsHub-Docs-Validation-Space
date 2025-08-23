## Description

When the user encounters **OH-Connector-0078**, then following error message will appear:  
**OH-Connector-0078**: Source Link is Hyperlink which cannot be mapped with Target Link &lt;&lt;Standard Link Type&gt;&gt; as &lt;&lt;Standard Link Type&gt;&gt; is a Link Type to link 2 existing entities in target side. Please correct the Relationship configuration to map 'Source Link Type' with any of the target Hyperlink.

**Example:**  
OH-Connector-0078: Source Link is Hyperlink which cannot be mapped with Target Link Child as Child is a Link Type to link 2 existing entities in target side. Please correct the Relationship configuration to map 'Source Link Type' with any of the target Hyperlink.

## Cause

When a Web Link is mapped with Standard Link, then incoming Web Link for synchronization in {{SITENAME}} will have limited details like link URL and link title. Standard Linkages are established based on issues that are synchronized by {{SITENAME}}. As Web Link does not have enough information to establish the Standard Linkage, this combination is not supported.
