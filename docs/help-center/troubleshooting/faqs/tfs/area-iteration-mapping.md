## Description

Area Path and Iteration Path are fields which contain values with Project name as a prefix, means in the format of "<Project Name>/<Whole Path of the Area/Iteration>". So in case TFS/Azure DevOps has been configured with different end system e.g. Jira, HP or in case source and target project is not identical when source and target endpoint is TFS/Azure DevOps, we need to do advance mapping where we need to remove the project name if the source endpoint is TFS/Azure DevOps and we need to add target project name as prefix if the target endpoint is TFS/Azure DevOps.

## Solution

Following are the examples to configure Area-Path when TFS/Azure DevOps is one of the end point. Click [View/Edit XSLT Configurations options](../../../../integrate/mapping-configuration.md#view-edit-xslt-configurations-options) and put following advance mapping:  

* To configure mapping when TFS/Azure DevOps is source end point and target end point is other than TFS/Azure DevOps. E.g. To configure mapping between TFS/Azure DevOps Area-Path field to Jira Sprint field following mapping can be used:  

```xml
<Sprint>
  <xsl:value-of xmlns:xsl="http://www.w3.org/1999/XSL/Transform" select="substring-after(SourceXML/updatedFields/Property/Area-space-Path,'\')"/>
</Sprint>
```

* To configure mapping when TFS/Azure DevOps is target end point and source end point is other than TFS/Azure DevOps. E.g. To configure mapping between Jira Sprint to TFS/Azure DevOps Area-Path field following mapping can be used:  

```xml
<Area-space-Path xmlns:xsl="http://www.w3.org/1999/XSL/Transform">
  <xsl:variable name="targetProjectName">
    <xsl:choose>
      <xsl:when test="SourceXML/opshubProjectName = '<Source Project Name>'">
        <xsl:value-of select="'<Target Project Name>'" />
      </xsl:when>
      <!--<xsl:when test="SourceXML/opshubProjectName = '<Source Project Name2>'">
        <xsl:value-of select="'<Target Project Name2>'" />
      </xsl:when>-->
    </xsl:choose>
  </xsl:variable>
  <xsl:choose>   
    <xsl:when test="SourceXML/updatedFields/Property/Sprint =''''">  
      <xsl:value-of select="$targetProjectName"/>
    </xsl:when>   
    <xsl:otherwise>  
      <xsl:value-of select="concat($targetProjectName,'\',SourceXML/updatedFields/Property/Sprint)"/>
    </xsl:otherwise>  
  </xsl:choose>
</Area-space-Path>
```

>**Note**: Uncomment line number 7 to 9 in case you have configured 2 projects. Repeat line 7 to 9 (when clause) based on the number of projects you have configured.

* To configure field mapping for between TFS/Azure DevOps Area-Path fields then following mapping can be used:  

```xml
<Area-space-Path>
  <xsl:choose xmlns:xsl="http://www.w3.org/1999/XSL/Transform">   
    <xsl:when test="SourceXML/updatedFields/Property/Area-space-Path !='<Source Project Name>'">  
      <xsl:value-of select="concat('<Target Project Name>\', substring-after(SourceXML/updatedFields/Property/Area-space-Path ,'\'))"/>  
    </xsl:when>   
    <xsl:otherwise>  
      <xsl:value-of select="'<Target Project Name>'"/>  
    </xsl:otherwise>  
  </xsl:choose>
</Area-space-Path>
```

Replace `<Source Project Name>` and `<Target Project Name>` with source and target project names respectively which have been selected during [Integration Configuration](integration_configuration) under **Select Project to Sync** section.

Similar above mapping is applicable for Iteration Path also, you need to replace `Iteration-space-Path` with `Area-space-Path`.
