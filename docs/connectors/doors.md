# Pre-requisites

## User privileges
* Create one user of DOORS System, dedicated to OpsHub Integration Manager. User should not be used to do any operations from system's user interface.
* User should have Read (R), Modify (M), Create(C) access rights for each module of the project that required synchronization. For more details on setting access rights, please refer [How to add permissions on module](#how-to-add-permissions-on-module) in appendix.

## DOORS client
* Install DOORS client on the machine where OpsHub Integration Manager is deployed (Recommended) OR install DOORS client on machine where OpsHub DOORS services can be configured (This machine should be in the same network of DOORS server).
* Tested on Operating Systems (OS): Windows XP, Windows 7, Windows 8.1, Windows Server 2012, Windows 10

## Set Log On User for OpsHub Server Service

If you had installed OpsHub Integration Manager on a Windows machine and you are running OpsHub Integration Manager through service, then in some cases, it may be possible that service account doesn't have access to DOORS client. In this case, you will not be able to access DOORS on OpsHub Integration Manager and you will get error related to DOORS connection. To resolve this issue, you may need to set log on user for OpsHub Server Service to the Windows user who has access to the DOORS client.

Please click here to learn -- how to [Set Log On User for OpsHub Server Service](#set-log-on-user-for-opshub-server-service).

## Restart OpsHub Integration Manager on DOORS metadata change

If any field/project added/renamed/deleted or access rights of fields/projects are changed:

- If DOORS service configuration is set as 'LOCAL' in OpsHub Integration Manager, DOORS server needs to be restarted.
- If DOORS service configuration is set as 'REMOTE' in OpsHub Integration Manager, OpsHub DOORS Services need to be restarted.

### For OLE Object

- OpsHub Integration Manager supports synchronization of OLE Objects when DOORS is a source system but for Microsoft Office document (.docx, .xlsx, .pptx, .doc, .xls, .ppt etc.) type of OLE Objects, Microsoft Office 2007 or higher must be installed on the machine where OpsHub Integration Manager is installed.
  - If Microsoft Office is not installed and a Microsoft Office file (such as .docx, .xlsx) are added from a system which has Microsoft Office installed and OpsHub Integration Manager instance does not have it installed, then only Microsoft Office icon will sync as inline image and the actual file will not get synchronized to target.
- OpsHub Integration Manager supports synchronization of OLE Objects when DOORS is a source system but for Microsoft Visio Drawing (.vsdx, .vsd) type of OLE Objects, Microsoft Visio 2013 or higher must be installed on the machine where OpsHub Integration Manager is installed.
  - If Microsoft Visio is not installed and a Microsoft Visio drawing file (such as .vsdx, .vsd) are added from a system which has Microsoft Visio installed and OpsHub Integration Manager instance does not have it installed, then such files will not get synchronized to target.

### For Rich Text Formatting

DOORS system allows users to add Rich Text formatting to Text/String type of fields. OpsHub Integration Manager supports synchronization of such formatting to target end system if following prerequisites are met:

- For support of full Rich Text, a conversion server is needed. The user needs to configure the conversion server and set its URL in [DOORS System Configuration](#system-configuration) of OpsHub Integration Manager. The conversion server must be up and running for usage in OpsHub Integration Manager.
- The [Documents4J Remote Conversion Server](https://documents4j.com/#/) is being used as the Rich Text Conversion Server. For the configuration of this Remote Converter Server, refer to sub-section **Microsoft Word Converter** in the section **Local converter** [here](https://documents4j.com/#/).
- This Rich Text Conversion Server can be set up on the machine where OpsHub Integration Manager is installed or on any remote machine where it can be accessed by the OpsHub Integration Manager setup machine. Refer to [Rich Text Conversion Server configuration](#rich-text-conversion-server-configuration) to set up the Rich Text Conversion Server. It is recommended to keep both on same machine to avoid the maintenance and network communication.

- Following are the prerequisites to set up the Rich Text Conversion Server:
  - A licensed Microsoft Word instance with version 2007 or higher is required to be installed. The user must ensure that the proper licensing and compliance terms for Microsoft Word are met completely. Also, Microsoft Word is properly activated and configured for the user who will be starting the OpsHub Integration Manager server.
  - The installed Microsoft Word instance must be set as the default app for opening and editing .rtf as well as .docx documents. Refer to [this guide](https://support.microsoft.com/en-us/windows/change-default-programs-in-windows-10-e5d82cad-17d1-c53b-3505-f10a32e1894d#:~:text=On%20the%20Start%20menu%2C%20select,set%20them%20as%20the%20default) to set defaults for an app.
  - Ensure that this Microsoft Word instance is dedicated to the Rich Text Conversion Server only when it is up and running (i.e., before starting the server. When the Rich Text Conversion Server is running, make sure that Microsoft Word is not already open before starting the Rich Text Conversion Server and OpsHub Integration Manager server).

> **Note** Synchronization of such full Rich Text formatting (i.e., tables, text highlights, font size, and colors, etc.) is only supported when DOORS is the source endpoint. In case the prerequisites are not met, or DOORS is the target endpoint, then only the formatting which is possible to perform from the DOORS UI will be synchronized.

# System Configuration

Before you continue to the integration, you must first configure the DOORS system. Click [System Configuration](../integrate/system-configuration.md) to learn the step-by-step process to configure a system. Refer to the screenshot given below for reference.  
![DOORS Image](DOORS_Image_6f.png)

<span style="color:blue">**DOORS System form details**</span>

| **Field Name** | **When field is visible on the System form** | **Description** |
|----------------|----------------------------------------------|------------------|
| **System Name** | Always | Provide System name |
| **Version** | Always | Set Version to version of your IBM Rational DOORS instance. |
| **DOORS Service Configuration** | Always | Location where OpsHub's DOORS Services are configured. i.e., 'LOCAL' or 'REMOTE'. |
| **Database Server Host** | When DOORS service configuration is set as 'LOCAL' | Set Database Server Host to the host name/IP Address where DOORS Database Server is hosted |
| **Database Server Port** | When DOORS service configuration is set as 'LOCAL' | Set Database Server Port to the port used by DOORS Database server (default: 36677). Specify another port if applicable. |
| **User Name** | When DOORS service configuration is set as 'LOCAL' | Set User Name to the name of the user account being used in the synchronization |
| **User Password** | When DOORS service configuration is set as 'LOCAL' | Set User Password to the corresponding password of the user account being used in the synchronization |
| **Client Path** | When DOORS service configuration is set as 'LOCAL' | Absolute DOORS client Path on the machine where OpsHub is installed, e.g. `C:\Program Files (x86)\IBM\Rational\DOORS\9.2\bin` |
| **Service Host** | When DOORS service configuration is set as 'REMOTE' | Host address where OpsHub's DOORS services are configured. Example: `10.10.10.1` |
| **Service Ports** | When DOORS service configuration is set as 'REMOTE' | Host ports where OpsHub's DOORS services are configured. Example: `4454,4456` |
| **DOORS File Server** | When DOORS service configuration is set as 'REMOTE' | URL where OpsHub's file server for DOORS is configured. Example: `http://localhost:8990` |
| **DOORS File Server User** | When DOORS service configuration is set as 'REMOTE' | Username for accessing DOORS file server |
| **DOORS File Server Password** | When DOORS service configuration is set as 'REMOTE' | Password for the above file server user |
| **DOORS File Server Base Folder** | When DOORS service configuration is set as 'REMOTE' | Path for file server's base folder. Example: `C:/OIMDoorsService` |
| **Rich Text Conversion Server URL** | Always | URL to convert DOORS RTF to HTML. Example: `http://localhost:9898`. Restart OpsHub server after changing. |
| **Read Deleted Entities** | Always | Select Yes to include deleted entities in synchronization; No to exclude. Applicable when DOORS is the source. |
| **Base Project(s) or Folder(s)** | Always | Path(s) to load modules from. If empty, all DOORS modules are loaded. Multiple paths can be comma-separated. |
| **DXL Executable Path** | When DOORS service configuration is set as 'LOCAL' | Path from which DXL can be executed. Can be absolute or relative to DOORS Home Folder. |
| **Additional Parameters** | When DOORS service configuration is set as 'LOCAL' | Add parameters like `-home`, `keydb`, `certdb`, etc. Use space as delimiter. |
| **Concurrent Batch Server Limit** | When DOORS service configuration is set as 'LOCAL' | Number of concurrent batch servers. Default: 5. Tune based on system capacity. |
| **Maximum Retry Attempt For Getting Lock** | Always | Number of retry attempts if lock acquisition fails |
| **Sleep Time For Each Attempt Of Getting Lock** | Always | Wait time (in seconds) for each failed lock attempt |

To know the version of DOORS, refer to [Find version](#find-version)

If the system is deployed over HTTPS with a self-signed certificate, you must import the SSL certificate to access the system from OpsHub Integration Manager. Click [Import SSL Certificates](../getting-started/ssl-certificate-configuration.md) to learn more.

# Mapping Configuration

Map the fields between DOORS and the other system to ensure correct synchronization. Click [Mapping Configuration](../integrate/mapping-configuration.md) for detailed instructions.

## Synchronization of formatting present in style attribute

When DOORS is the target system:
- DOORS cannot render style attributes of HTML.
  - This often happens when content is copied from Word, Excel, etc., into the source system.
- To preserve formatting, OpsHub Integration Manager provides a utility method:  
  **`convertStyleAttributeToHTMLTags`**
  - This converts inline style attributes into supported HTML tags.

Example mapping from **TFS `Repro Steps`** field to **DOORS `Object Text`**:
```xml
<Object-space-Text>
  <xsl:value-of xmlns:xsl="http://www.w3.org/1999/XSL/Transform" 
    select="utils:convertStyleAttributeToHTMLTags(SourceXML/updatedFields/Property/Repro-space-Steps)" />
</Object-space-Text>
```

Supported formatting (converted from style to HTML):
- **Bold**
- **Italic**
- **Underline**
- **Strikethrough**
- **Subscript**
- **Superscript**

## Rank

DOORS supports hierarchical (tree) structure for requirements. To preserve this:

- Map `OH_ChildIds` and `OH_ParentId` per [Relationship Configuration](../integrate/mapping-configuration.md#relationship-configuration).
- Enable rank sync as described in [Rank configuration](../integrate/mapping-configuration.md#rank-configuration).

# Integration Configuration

Configure integration time, sync parameters, and conditions. See [Integration Configuration](../integrate/integration-configuration.md) for setup steps.

## Event Detection & Generation

- DOORS supports event detection using the **Object Number** attribute.
- Note: Object Number updates (e.g., move, add, remove) **do not** update the "Last Modified Time".
- If DOORS is the **source system** and **history-based sync** is used:
  - You must provide **additional user credentials** (not same as integration user).
  - These credentials will update the object on detection.
  - **Not required** for current-state sync.

> ⚠️ **Important:**  
> Additional credentials must:
> - Be different from the integration user  
> - Be dedicated for OpsHub Integration Manager  
> - Not be used for regular operations in DOORS

**Limitations:**  
- Object movement events will not be detected in the following cases:
  1. Object is purged from DOORS
  2. Baseline is deleted from DOORS

# Criteria Configuration

Define criteria per integration requirements.

## Query

- A **query** in DOORS filters data based on attributes.
- In OpsHub Integration Manager, provide the DOORS-compatible query.

### Sample Query Snippets

| **Syntax** | **Description** | **Example** |
|------------|-----------------|-------------|
| `(attribute 'attr' operator 'text')` | Comparison on fields like Status, Last Modified, Created By | `(attribute 'Status' == 'Active')`<br>`(attribute 'Last Modified On' > '05/25/2018')`<br>`((attribute 'Status' == 'Active') && (attribute 'Created By' == 'User1'))`<br>`((attribute 'Status' == 'Active') || (attribute 'Created By' == 'User1'))` |
| `includes(attribute 'attr', 'text')` | Filter for multi-valued attributes | `includes(attribute 'MultiProject','Project1')` |
| `excludes(attribute 'attr', 'text')` | Exclude values from multi-valued attributes | `excludes(attribute 'MultiProject','Project1')` |
| `((attribute 'attr' operator 'text') && includes(attribute 'attr', 'text'))` | Combined query | `((attribute 'Status' == 'Active') && includes(attribute 'MultiProject','Project1'))` |

### Criteria Using Special Characters

* While using `'` (single quote) in query, user will have to provide the escaping for it. i.e., the character `\'` should be used instead of `'` wherever needed.
  * **Example**: `(attribute 'Object Heading' == 'This object contains \' in Heading')`
  * In DOORS: `This object contains ' in Heading`
  * In OpsHub Integration Manager: `This object contains \' in Heading`

---

# Configure OpsHub's DOORS Remote Services

When user wants to install OpsHub's DOORS Remote Services on any machine (which is locally connected with a machine having DOORS Server configured), the below steps need to be followed:

* Download "OpsHub DOORS Remote Service utility" from [here].
* This utility requires the following files to be copied from:  
  `(OIM installation directory)\OpsHubServer\webapps\OpsHubWS\WEB-INF\classes\com\opshub\eai\doors\common\resources`  
  to utility's `resources` folder:
  * `OIM_DoorsBatchServer_Template.dxl`
  * `OIM_DoorsScripts.dxl`
* Fill the configuration data in `resources/config.properties`:

<table style="margin: auto;">
<tr><th>Field Name</th><th>Description</th></tr>
<tr><td><code>protocol</code></td><td>Enter protocol type to be used by File Server. The File Server can run on http/https.</td></tr>
<tr><td><code>port</code></td><td>Enter port to be used by File Server.</td></tr>
<tr><td><code>keyStorePath</code></td><td>Only considered for https. You can use CA-certified or self-signed certificate.<br>Sample:<br><code>keytool -genkeypair -alias OIMFileServerCert -keyalg RSA -keysize 2048 -validity 365 -storetype PKCS12 -keystore keystore.p12</code></td></tr>
<tr><td><code>resourceBase</code></td><td>Directory path whose files/folders can be served as resources.</td></tr>
<tr><td><code>userName</code></td><td>User for file web server.</td></tr>
<tr><td><code>dbHost</code></td><td>Host/IP of machine where DOORS DB server is running.</td></tr>
<tr><td><code>dbPort</code></td><td>Port on which DOORS DB server is running. Example: 36677</td></tr>
<tr><td><code>dbUser</code></td><td>DOORS DB user with Read (R), Modify (M), Create (C) rights for synced modules.</td></tr>
<tr><td><code>doorsClientPath</code></td><td>Absolute DOORS client path. Example:<br><code>C:/Program Files/IBM/Rational/DOORS/9.2/bin/doors.exe</code></td></tr>
<tr><td><code>servicePorts</code></td><td>Ports on which DOORS services need to be configured. Example: <code>4454,4456</code></td></tr>
<tr><td><code>additionalParams</code></td><td>Any additional command-line params (e.g., <code>-home "C:/Program Files/IBM/Rational/DOORS/9.6"</code>)</td></tr>
</table>

## To run the Utility:

1. Open Command Prompt as Administrator.
2. Navigate to the utility folder.
3. Run: `OpsHubDoorsRemoteServiceUtility.bat`

---

# Known Synchronization Behavior

## Picture Object as Inline Image

* Supported only when DOORS is the **source** system.
* Map the **Picture** field in OpsHub Integration Manager.
* Image changes sync only if some other revisioned field is updated.
* Some pictures may export with **black border** (DOORS API limitation).
* Only **PNG** format is supported.

---

## Object Number and Object Level

* These are **calculated fields**. OpsHub Integration Manager syncs their current value only.
* Values depend on the DOORS system config:
  * If **Sync Deleted Entities** = `yes`, deleted entries are considered.
  * If `no`, deleted entries are ignored.

---

## Fields Limitation

* `RTF NonShpPict` and `RTF ShpPict` fields **not supported** due to large binary content and performance issues.

---

## OLE Object as Inline Image/Document

* Not supported via **Reconciliation**.
* Supported only when **DOORS is source**.
* Behavior:
  * Target shows the **latest revision only**.
  * History of OLEs not maintained.
* **Microsoft Excel** OLE:
  * Data may be hidden. Open → View Tab → Unhide → Save.
* **Open Office**:
  * `.odp`, `.odt` are supported. Use Microsoft Office to open.
  * Other OpenOffice types may appear corrupted.
* If **any OLE file > 20MB**, none will sync; only text will.
  * Message:  
    `#DOORS OLE(s) data is not synchronized, as one of the OLE size is too big (approx more than 20MB)#`
* **BMP or Paintbrush OLEs** always sync as **inline documents**.
* **Open/Old Office formats** may cause **attachment mismatches** if similar files exist.
* Supported file formats:  
  `.bmp, .png, .jpg, .jpeg, .gif, .ico, .exe, .jar, .cer, .properties, .txt, .mkv, .3g2, .3gp, .avi, .flv, .mov, .mp3, .mp4, .webm, .wmv, .pdf, .odp, .odt, .docx, .xlsx, .pptx, .vsdx, .doc, .ppt, .xls, .vsd, .pptm, .xlsb, .dll, .java, .apk, .7z, .zip, .css, .dat, .eml, .log, .xml, .yaml, .html, .htm, .xhtml`

* For `.rtf` and `.csv`:  
  * `.rtf` → `.doc`, `.csv` → `.xlsm` in target.
* OLE shown as “Picture (Enhanced Metafile)” → appears blank (API limitation).

> **Note** :If syncing other formats, validate in test environment. Contact OpsHub Support for help.

---

## Synchronizing Rich Text Data with Full Formatting

* Full formatting supported only when **DOORS is source**.
* RTF formatting is synced only in **last revision**.
* Copied tables with border=0 → borders may not appear in target.
* If **RTF Server URL** changes:
  * Update in OpsHub Integration Manager DOORS config page.
  * Restart server.
* For links in RTF fields:
  * Only URLs sync, not link text.
* **Conflict detection** might have false positives for HTML with advanced tags.

> **Note** : To verify formatting: see section *Verify output of Rich Text conversion from Rich Text Conversion Server*.

---

## Synchronizing Entities with Deleted History

When DOORS is the source:
* If the entity history is deleted **and** last modified by integration user → entity will **not** sync.
  * Example: **Baseline deletion**
* Best practice: let sync finish first, then delete history.

---

# Appendix

## DOORS Reserved Keywords (Do Not Use as Field Names)

The following field names are **reserved** and must **not** be used in DOORS:

```
OH_ModuleName
OH_eventType
OH_ObjectURL
OH_objectId
OH_CreateUpdateTime
OH_attributeName
OH_oldValue
OH_newValue
OH_oldRtfValue
OH_newRtfValue
OH_ParentId
OH_OldBaseline
OH_NewBaseline
OH_discussionTitle
OH_discussionCreator
OH_discussionCreationTime
OH_commentBody
OH_commentCreator
OH_LAST_MODIFIED_TIME
OH_UpdatedBy
OH_Baseline
OH_OutLink
OH_InLink
```

---

## Custom Field Configuration

1. Log in to DOORS desktop client with **admin access**.
2. Open the module to add field.
3. Menu: `Edit → Attributes`

<p align="center">
  <img src="DOORS_Image 1.png" alt="Attribute Window" />
</p>

4. Click **New**, set name (not from reserved list), type, and default value if needed.

<p align="center">
  <img src="DOORS_Image 2.png" alt="Create Attribute" />
</p>

5. Click **OK**, then **Save** the module.

---

## How to Add Permissions on Module

1. Login to DOORS desktop client with admin rights.
2. Right-click the target module → **Properties**.
3. Go to the **Access** tab → assign proper rights.

<p align="center">
  <img src="DOORS_Image 3.png" alt="Set Access" />
</p>

## Find version
* Login into DOORS desktop client.
* Navigate to help menu, and click **About DOORS**

![DOORS_Image 4.png](DOORS_Image 4.png)

* It will open a separate window that will show DOORS server version.

![DOORS_Image 5.png](DOORS_Image 5.png)

## Notes on Custom Field sync
* Custom Field that requires to be synced must have 'Attribute scope' as Objects or Objects & Module (Only 'Module Scope attribute' can't be synced)
* DXL Attribute can only be used for reading; such attributes can't be written.
* DXL Attribute doesn't have any history, so when other fields are changed and OpsHub Integration Manager syncing those events, the value of the DXL attribute as of sync time will be sync to target.

Learn how to create [Custom Field Configuration](#custom-field-configuration).

## OLE configuration
* To sync OLE object data, you need advance configuration for the field that is mapped with OLE type field. The sample XSL for the configuration is given below:  
This is the sample XSL:  
```
<@description@ xmlns:xsl="http://www.w3.org/1999/XSL/Transform" >
  <xsl:element name="oleFieldValue">
    <xsl:value-of select="SourceXML/updatedFields/Property/@Object-space-Text@/oleFieldValue"/>
  </xsl:element>
  <xsl:if test="SourceXML/updatedFields/Property/@Object-space-Text@/oleAttachments">
    <oleAttachments>
      <xsl:for-each select="SourceXML/updatedFields/Property/@Object-space-Text@/oleAttachments/OHAttachment">
        <xsl:element name="{concat('attachment_',position())}">
          <filename><xsl:value-of select="fileName"/></filename>
          <contentLength><xsl:value-of select="contentLength"/></contentLength>
          <attachmentURI><xsl:value-of select="attachmentURI"/></attachmentURI>
          <attachmentReferenceType><xsl:value-of select="attachmentReferenceType"/></attachmentReferenceType>
        </xsl:element>
      </xsl:for-each>
    </oleAttachments>
  </xsl:if>
  <OLE.Object-space-Text>
    <OH_Embedded.OLE>true</OH_Embedded.OLE>
    <OH_Embedded.Picture>true</OH_Embedded.Picture>
    <OH_Embedded.Reference>true</OH_Embedded.Reference>
  </OLE.Object-space-Text>
</@description@>
```

* Change the XSL according to your environment. In the given case, the source field is an 'Object Text' and the Target Field is 'Description'. Therefore, we need to make changes in XSL according to the field mapped in the source and the target systems.
* Content we need to replace in above XSL is highlighted in the format shown below:
  * For source field: `@Object-space-Text@`
  * For Target field: `@description@`
* In the above XSL - OLE, picture and reference to the OLE file is configured. If we don't want the reference or picture object to sync, you need to pass 'false' value. For eg: `<OH_Embedded.Picture>false</OH_Embedded.Picture>`.

## Rich Text Conversion Server configuration
The Rich Text Conversion Server communicates with the Microsoft Word instance, which performs the actual conversion for the supplied Rich Text. To configure this server, following steps need to be followed:

* Download the `documents4j-server-standalone-shaded.jar` from [here](https://documents4j.com/#/) from the *Download* sub-section in the *Getting documents4j* section;
* Open the Command Prompt and run the below command to configure and start the Rich Text Conversion Server (make sure that the user has sufficient privileges to access below folders, else open Command Prompt as Administrator):

```
<OpsHub Integration Manager installation path>\OpsHub_Resources\jre\bin\java -jar <path_to_jar>\documents4j-server-standalone-shaded.jar http://<host_address>:<port_no>
```

* For example, if the port number is selected as 9998 to be configured locally, then the command will be:

```
"C:\Program Files\OpsHub\OpsHub_Resources\jre\bin\java" -jar "C:\Downloads\documents4j-server-standalone-shaded.jar" http://localhost:9998
```

* If the Rich Text Conversion Server is set up on a separate machine, then while using the above command, the user needs to input the IP Address of that machine instead of localhost. For example:

```
"C:\Program Files\OpsHub\OpsHub_Resources\jre\bin\java" -jar "C:\Downloads\documents4j-server-standalone-shaded.jar" http://10.13.28.123:9998
```

* The configured URL for this server needs to be given on the [DOORS System Configuration](#system-configuration) page.

## Recommended Practices
To ensure the document4j's server functions correctly:

1. Do not open or close Microsoft Office on the same server machine where document4j is running. Doing so can cause document processing failures and can lead to errors such as:

```
com.documents4j.throwables.ConverterAccessException: The converter could not process the request.
```

2. To resolve the `ConverterAccessException`, you need to restart the document4j's server.

By following these practices, you can avoid errors and ensure smooth operation of the Document4j server.

### Verify output of Rich Text conversion from Rich Text Conversion Server
To verify the output of Rich Text conversion and visualize how the text will be displayed in the target system, a DXL script needs to be executed. This DXL script will download an RTF file at the specified location. This file can then be provided to Microsoft Word to convert to HTML to verify the output of the conversion. The resultant HTML file will display how the Rich Text displays in the target system. Here is the DXL:

```dxl
Module initModule(string modulePath){
    Module m = read(modulePath,false)
    View v= view("Standard view")
    load(m,v)
    showDeletedObjects(true)
    showTables(true)
    return m
}

string downLoadRTFFile(int objectId,string modulePath, string doorsResourcePath,string attributeName)
{
    noError()
    string error = null
    Module m = initModule(modulePath)
    Object o = object(objectId,m)
    string response =  ""
    string isSuccess="false"
    EmbeddedOleObject ole
    string s = ""
    RichText rtf
    s = richTextWithOle o.attributeName
    Stream oStream = write(doorsResourcePath)
    oStream << s
    close(oStream)
    isSuccess = "true"
    close(m)
    if(error==null)
        error = lastError()	
    response = isSuccess
    return response
}

downLoadRTFFile('''<object_id>''', '''"<module_path>"''', '''"<absolute_path_to_download>"''', '''"<name_of_rich_text_supporting_field>"''')
print "DONE"
```

Steps to execute and verify:

1. To execute this DXL, open the DOORS UI, click on **Tools** menu and select **Edit DXL...**;
2. Copy the above DXL and paste it into the DXL input in the DXL Editor;
3. Modify the arguments for the `downLoadRTFFile` function call in the following order:
   1. `object_id`: The id of the object for which RTF file has to be downloaded;
   2. `module_path`: The full path of the module in which the object is present, e.g. if the object is in `/QA/QA Module`, then input should be the full path;
   3. `absolute_path_to_download`: The path where the file has to be downloaded, e.g. `C:/Users/Admin/Downloads/SampleFile.rtf`;
   4. `name_of_rich_text_supporting_field`: The field display name for which the file has to be downloaded, e.g. `Object Text`;
4. Click on **Run** to execute the DXL. If the download is successful, `DONE` will be printed in the DXL output window and an RTF file will be generated;
5. Open the generated RTF file in Microsoft Word. Go to **File > Save As**, then save the file as HTML;
6. Open the saved HTML file. This file's output shows how the field's data will be displayed in the target system.
