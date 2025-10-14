# Overview
This section will guide the users on how to register and edit the connectors.

# Register Connectors
Connectors can be registered from the administration page by clicking the "plug" icon <img src="../assets/RegisterConnectorIconOnly.png" alt="Register Connector Icon" width="25"/> present in the left sidebar as shown in the image below:

<p align="center">
  <img src="../assets/AddButtonRegisterConnector.png" width="1200"/>
</p>

To register a connector, click the "+" icon on the top right corner of the "Registered Connectors" page.  
The following page appears which requires two inputs as shown in the image below:

<p align="center">
  <img src="../assets/RegisterConnectorPage.png" width="1200"/>
</p>


Fill the form with relevant details:  

- **System Type Name**: The name that you want to assign to the connector you are registering. This name will be shown in the system type list on the "Configure Systems" page.  
- **SDK API Base URLs**: Base URL of the Connector SDK where it is hosted. E.g., `http://<hostname>:<port>/sdk-api/api/1.0`. You can add more than one SDK URL for a given connector using the "+" icon on the right side of the text box. The first URL entered will be used for fetching the metadata of the connector. All the SDK API calls will be made by appending the resource path to this URL.  

All the URLs entered will be checked if they are implemented with the same connector's name and version or not.  

After entering valid details, click the **Save** button to register the connector with the given name.

>**Note**: System Type Name must be unique as <code class="expression">space.vars.SITENAME</code> won't allow you to use the same name for registering the connector.

# View Connectors
The registered connectors are available in the form of a list on the "Registered Connectors" page as shown in the image below:

<p align="center">
  <img src="../assets/RegisterConnectorList.png" width="1200"/>
</p>

There is an audit icon ![Audits Icon](../assets/AuditsIcon.png =25x) present on the top right corner of the list. Clicking this icon will show all the audits related to the registered connectors.

# Edit Connectors
Registered connectors can be edited by clicking the specific connector followed by clicking the pencil icon on the top right corner of the page:

<p align="center">
  <img src="../assets/EditButton.png" width="1200"/>
</p>


You can edit the system name, add or remove URLs. There is also a checkbox in case you want to refresh the metadata of the connector:

<p align="center">
  <img src="../assets/RefreshConnectorMetadataCheckBox.png" width="1200"/>
</p>


>**Note**: Edit register connector option will not allow you to remove the URL if it is already used in any system or in the integration of the systems. An error message will be displayed if the URL that is already in use is deleted.

## Refresh Connector Metadata
The **Refresh Connector Metadata** checkbox (as shown in the image above) can be selected under the following condition:  

- Whenever there is any change (addition or deletion) of metadata in the connector.

While editing the connector, if the refresh connector metadata is checked, a warning pops up as shown in the image below:

<p align="center">
  <img src="../assets/RefreshMetaData.png" width="800"/>
</p>


>**Note**: If you want to refresh metadata for a connector, it is advisable to verify the systems and integrations that will be affected.  

This warning box contains instructions on how the systems and integrations created on the connector will be affected if you choose to refresh the metadata. As shown in the image, this warning also shows the particular field that is removed and the screens affected by it.


