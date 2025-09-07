# Pre-requisites

## User privileges
* Create one user for Micro Focus ALM/QC, dedicated to {{SITENAME}}. This user should not do any other operations from the Micro Focus ALM/QC's user interface. For creating user, please refer [Add User to Project](https://admhelp.microfocus.com/alm/en/12.60/online_help/Content/Admin/cust_users_add_to_proj.htm). 
* Micro Focus ALM/QC user must be an **Active site user** in Micro Focus ALM/QC. If the user is deactive user in Micro Focus ALM/QC, then activate the user. For help on how to activate the user, please refer [Activate the User](#Activate-the-User-as-a-Site-User) in Appendix.
* To use a particular project in Micro Focus ALM/QC, the user must be present as a **Project User** for that project. For help on how to add a project user in the project, please refer [Add project user in project](#Add-project-user-in-project) in Appendix.
* Micro Focus ALM/QC user must have **Project Administrator** rights on the Project that is to be synchronized. For help on how to set the access rights on project, please refer [Add Permissions To Project](#Add-permissions-to-project) in Appendix.  
>**Note**: In case your Micro Focus ALM/QC is configured with SSO, then the above mentioned User privileges and permissions are sufficient.

## Database prerequisites
* For Micro Focus ALM/QC Quality Center 10 and 11, supported database types are: MS SQL Server and Oracle.

## System prerequisites
* For OpenText ALM Quality Center version 24.x:
  * Add the site parameter **ENABLE_GET_LOGOUT_METHOD** and its value to **Y**. To perform this action, go to `http://IP:PORT/qcbin/webadmin/#/configuration` and click on **Add New Parameter**.
    * Reason: Logout user API will not work without this site parameter.  

<p style="center">
  <img src="../assets/HPAML_QC_addSiteParam.png" />
</p>

## Proxy configuration
For certain Micro Focus ALM/QC versions, proxy configuration is required only for specific types of data synchronization, such as:  
* For version 10.0, 11.0, and 11.5: Required only when design steps or requirement traceability need to be synchronized.  
* For version 12.0: Required only when design steps need to be synchronized.  

**Required for all versions:**  
* To synchronize test set execution.  
* To synchronize attachments in cycle entity.  
* To read actual values of parameters for different test configurations in test entity.

| **CPU** | Core duo 1.6 Ghz (or higher) or equivalent compatible processor |
|---------|----------------------------------------------------------------|
| **Memory (RAM)** | 4 GB (recommended) |
| **Operating system (Tested On)** | Windows 7, Windows 10, Windows Server 2008, Windows Server 2012, Windows Server 2016, Windows Server 2019 |
| **Software** | * Visual C++ 2005 SP1 ATL Security Update Redistributable <br> * Microsoft .NET Framework 4.5 (SP1) <br> * IIS 7.0 with ASP.NET configured <br> * Micro Focus ALM/QC Connectivity Add-in (Download from: `http://<Micro Focus ALM/QC host>:<port>/qcbin/addins.html`) |
>**Note**:  For Test Set Execution Request integration, the OpsHub ALM/QC Proxy must be configured on a machine on which UFT has been installed.  
Click here for [Proxy Configuration steps](#Proxy-Configuration-steps).

## Configurations required to copy QTP script
Following additional configurations are required to copy QTP script:  
* **Quick Test Professional** and appropriate **QuickTest Professional Add-In** must be installed on the machine on which OpsHub ALM/QC proxy is configured. To download QuickTest Professional Add-In, please follow [this link](https://hpln.hp.com/page/quicktest-professional-add).

## Enable history of fields to be mapped
* It is recommended to enable history at least on those fields that are going to be mapped in the integration for {{SITENAME}} and on **Modified** field to ascertain whether any modifications are made on a particular field. Click [Enable history of fields to be mapped](#How-to-enable-history-of-fields-to-be-mapped) to learn the steps.  
* If Micro Focus ALM/QC is the target system, then integration recovery will not work if the history has not been enabled. The integration recovery can, in fact, create duplicate entities in Micro Focus ALM/QC. Integration will throw error before performing create/update if history has not been enabled on any mapped field.  
* If Micro Focus ALM/QC is the source system and history has not been enabled, then integration needs to be configured in **Current State Sync** mode only. You can learn about **Current State Sync** mode from [here](../integrate/integration-configuration#sync-only-current-state).

## Associate a custom field with the Requirement
* For the **Requirement** entity, if user wants to use a custom field in mapping, then the custom field must be associated with all the Requirement Types that will be used in the mapping.  
* Click [How to associate a custom field with Requirement](#How-to-associate-a-custom-field-with-Requirement) to know the steps.

# System Configuration
Before you continue to the integration, you must first configure Micro Focus ALM/QC.  
Click [System Configuration](../integrate/system-configuration.md) to learn the step-by-step process to configure a system.  
Refer the screenshot given below for reference.

<p align="center">
  <img src="../assets/HPALM_Image_2F1aa.png" />
</p>


| **Micro Focus ALM/QC System Form Details** |  |  |
|-------------------------------------------|--|--|
| **Field Name** | **When Field is Visible on the System Form** | **Description** |
| System Name | Always | Provide Micro Focus ALM/QC System Name. |
| Version | Always | Put the version for the Micro Focus ALM/QC. |
| Server URL | Always | Provide server URL of the Micro Focus ALM/QC instance. This URL will be used for connecting to Micro Focus ALM/QC API. Format: `http://<host name>:<port no>/qcbin` Example: `http://myopshub:1234/qcbin`. |
| OpsHub ALM/QC Web Service proxy URL | Always | Proxy configuration is required only for specific types of data synchronization. For more details navigate to [proxy configuration](#Proxy-configuration). Format for URL: `http://<host name>:<port no>/HPQCService.asmx`. |
| User Name | Always | Provide a dedicated user (enter User Name in this field) for API communication with your Micro Focus ALM/QC instance. This user should have the required privileges to use the Micro Focus ALM/QC API. |
| Password | Authentication Type is Basic | Provide the password for the user given in "User Name" field. |
| Client ID | Authentication Type is API key | Provide 'Client ID' of dedicated user (provided above) for API communication with your ALM/QC instance. This user should have the required privileges to use the Micro Focus ALM/QC API. Refer [Create API Key](https://admhelp.microfocus.com/alm/en/15.5-15.5.1/online_help/Content/Admin/api_keys_task.htm) to learn about how to create Client ID and API key secret. |
| API Key Secret | Authentication Type is API key | Provide the 'API key secret' for the Client ID provided above. Refer [Create API Key](https://admhelp.microfocus.com/alm/en/15.5-15.5.1/online_help/Content/Admin/api_keys_task.htm) to learn about how to create Client ID and API key secret. |
| Database Schema Name | Always | For certain Micro Focus ALM/QC versions, Database Schema Name is required only for specific types of data synchronization, such as: For version 11.0 and 11.5: Required only when requirement-traceability or design-steps needs to be synchronized. For version 12.0: Required only when design steps need to be synchronized. |
| Case Sensitive | Always | Set the case sensitive to specify whether Micro Focus ALM/QC User Name is case sensitive or not. |
