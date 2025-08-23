## Description

When migrating the history of the Pipeline entity, there can be processing failure for the following use case:

- **Use case:** "Service Connection 1" was associated in some steps of any job in the Pipeline entity. The user changed the Service Connection from "Service Connection 1" to "Service Connection 2" and deleted the "Service Connection 1" from the end system.  

In the above use case, the following error occurs:  
`OH-TFS/AzureDevOps-0088: Error occurred while executing request : <Request URL>, detailed Server response : {"$id":"1","innerException":null,"message":"The pipeline is not valid. Job <Job>: Step  input <Input Name> references service connection <Service Connection ID> which could not be found. The service connection does not exist or has not been authorized for use.<Other Error Data>}"`

## Solution

- If the Service Connection is deleted in the source system, there will be a processing failure in the integration.
- To resolve this failure, the Service Connection ID needs to be replaced with an empty value.
- For this replacement, the following XSLT can be used. In the field mapping, use the below advanced XSLT for the `process` field:

```xml
<process xmlns:xsl="http://www.w3.org/1999/XSL/Transform">
  <xsl:variable name="replaced0" select="SourceXML/updatedFields/Property/process"/>	
  <xsl:variable name="source1" select="'{Service Connection ID}'"/>
  <xsl:variable name="replaced1" select="utils:replace($replaced0,$source1,&#39;&#39;)"/>	
  <xsl:value-of select="$replaced1"/>
</process>
```
- For multiple Service Connections, extend the XSLT as follows:

```xml

<process xmlns:xsl="http://www.w3.org/1999/XSL/Transform">
  <xsl:variable name="replaced0" select="SourceXML/updatedFields/Property/process"/>	
  <xsl:variable name="source1" select="'{Service Connection ID-1}'"/>
  <xsl:variable name="replaced1" select="utils:replace($replaced0,$source1,&#39;&#39;)"/>
  <xsl:variable name="source2" select="'{Service Connection ID-2}'"/>
  <xsl:variable name="replaced2" select="utils:replace($replaced1,$source2,&#39;&#39;)"/>
  <xsl:variable name="source3" select="'{Service Connection ID-3}'"/>
  <xsl:variable name="replaced3" select="utils:replace($replaced2,$source3,&#39;&#39;)"/>
  <xsl:value-of select="$replaced3"/>
</process>
```