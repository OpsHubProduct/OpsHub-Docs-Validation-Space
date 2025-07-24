
# Description

When you encounter `OH-Aras-1502`, then the following error message will appear:
OH-Aras-1502: Error occur during add attachment for internalId : `<Entity_Id>`, file name :`<FileName>` file type :`<Entity_type>` File with message:`<Aras_Service_Error_Message>`.

**Example**: OH-Aras-1502: Error occur during add attachment for internalId : 099047AA6E92470C91D4EC43BCF27197, file name :Abc:Xyz.txt file type :Part File with message :Aras Web Service Error =Error occur while add attachment for internal id 099047AA6E92470C91D4EC43BCF27197, filePath : C:\Users\AppData\Local\Temp\OIM-8586062924948743403\Abc_Xyz.txt, fileType :text/plain, itemType : Part, fileName : Abc:Xyz.txt, Aras Error Code = and Aras Error Message = ".

---

# Cause

One of the reasons for the above error can be **Attachment Filename containing Windows special characters**  `[`, `]`, `/`, `\`, `"`, `:`, `*`, `?`, `<`, `>` . This is because **Aras does not support Windows special characters in filename**.

---

# Solution

If the Attachment filename contains Windows special characters (`[`, `]`, `/`, `\`, `"`, `:`, `*`, `?`, `<`, `>`), then add **Advanced Mapping for Attachment** such that we replace the special characters with any of the supported characters.

Below is a snippet for advanced mapping for attachment in which `:` (colon), `*` (asterisk), and `?` (question mark) are being replaced by `_` (underscore) in filename:

```xml
<OHAttachments>
  <xsl:for-each xmlns:xsl="http://www.w3.org/1999/XSL/Transform" select="SourceXML/updatedFields/Property/OHAttachments/OHAttachment">
    <xsl:element name="{concat('attachment_',position())}">
      <filename>
        <xsl:value-of select="translate(fileName,':*?', '___' )"/>
      </filename>
      <addedByUser>
        <xsl:value-of select="addedByUser"/>
      </addedByUser>
      <contentLength>
        <xsl:value-of select="contentLength"/>
      </contentLength>
      <contentType>
        <xsl:value-of select="contentType"/>
      </contentType>
      <contentBase64>
        <xsl:value-of select="contentBase64"/>
      </contentBase64>
      <attachmentURI>
        <xsl:value-of select="attachmentURI"/>
      </attachmentURI>
      <updateTimeStamp>
        <xsl:value-of select="updateTimeStamp"/>
      </updateTimeStamp>
      <label>
        <xsl:value-of select="label"/>
      </label>
      <fileComment>
        <xsl:value-of select="fileComment"/>
      </fileComment>
      <attachmentReferenceType>
        <xsl:value-of select="attachmentReferenceType"/>
      </attachmentReferenceType>
      <uniqueCode>
        <xsl:value-of select="uniqueCode"/>
      </uniqueCode>
      <attachmentType>
        <xsl:variable name="xPathVariable" select="attachmentType"/>
        <xsl:value-of select="attachmentType"/>
      </attachmentType>
    </xsl:element>
  </xsl:for-each>
</OHAttachments>
```
