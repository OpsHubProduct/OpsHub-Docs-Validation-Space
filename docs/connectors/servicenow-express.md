# Prerequisites

## User Privileges

* Create one administrator user in ServiceNow system, dedicated to integration. User should not be used to do any operations from ServiceNow User-Interface. In case if administrator user is not available, user should have access to following tables.

Access to below tables are required for Table REST API.

- `sys_attachment(ALL)`  
  *Used to get the attachment details and to delete attachment.*
- `sys_audit(read)`  
  *Used for getting the revision(history) information of entity.*
- `sys_db_object(read)`  
  *Used for getting entity meta information like the tables(entity) which can be supported in integration.*
- `sys_dictionary(read)`  
  *Used for getting fields meta information of any table(entity) like incident have short_description, description.*
- `sys_choice(read)`  
  *Used for getting choice values for lookup(dropdown) fields like priority have values 1.Low, 2.Medium.*
- `ecc_queue(Create-write)`  
  *Used for adding attachment to any table(entity).*
- `sys_attachment_doc(read)`  
  *Used for getting the attachment content.*
- `sys_user(read)`  
  *Used for getting meta information of users configured in ServiceNow like username, email-id.*
- `sys_journal_field(ALL)`  
  *Used for getting the comments added on table(entity) record.*
- `Sys_Transform_map(Read)`  
  *Used for getting the transformation map created in ServiceNow instance under OpsHub Integration Solution for ServiceNow.*
- `Sys_transform_entry(Read)`  
  *Used for getting the fields mapped in transformation map.*

* User should have access to all the entities that need to be synchronized

* In case if sufficient privileges are not there than following error will come while configuration or synchronization.  
  `ACL Exception Update Failed due to security constraints .`

## Turning on Auditing (History) for a table

* Audit must be enabled for Entity synchronization in integration. ServiceNow tracks incident, change, and problem history in the sys_audit table. [Enable Audit](#turning-on-auditing-for-a-table) tracks the creation, update, and deletion of audited records. Audit must be enabled on the Entity table (e.g. not to its import set table) 

## Enable Integration for ServiceNow instance

* Integration must be enabled for the ServiceNow instance. You can submit a request to enable this app from ServiceNow [Appstore](https://store.servicenow.com/sn_appstore_store.do#!/store/application/8e6f0b610f8ce6001f6fc3ace1050ebb).

![snow1](../assets/snow1.png)

* On the Integration App page, Click on Contact Seller and provide your ServiceNow HI Credentials

* Once your request is approved, you will see **OpsHub Integration Solution for ServiceNow** in Downloads Tab by navigating **System Applications -> Applications** in your ServiceNow instance [Below example shows Integration for ServiceNow Enterprise]. Click on Install for the OpsHub Integration Solution for ServiceNow applications

![snow2](../assets/snow2.png)

* On Successful installation, OpsHub Integration Solution for ServiceNow Application will be available

## Import-set Table

1. Import set table must be created for each entity to be used in Synchronization.
2. For a given actual table only one import-set table should exist under OpsHub application records.
3. Opshub import set table internal name should start with  `x_oph`.
4. The field type and the lookup value in import set table should be same as the field type and the lookup value in the actual table, with which the import set field needs to be mapped.
5. For reference field internal name should be same as target field.
6. Only reference field should be map with source script.
7. For fields in Import-set table, in Choice configuration under  Choice List Specification  do **not** select value **Dropdown without   None   (must specify a default value)**

For creating import set table under Integration Application refer _Import Set Table and Transformation Map_

# System Configuration

Before you continue to the integration, you must first configure ServiceNow system. Click [Step 1 - Configure Systems](http://opshubdocs.northcentralus.cloudapp.azure.com/oim/index.php/Step_1_-_Configure_Systems) to learn the step-by-step process to configure a system. Refer the screenshot given below for reference.

![snow3](../assets/snow3.png)

* Set **System Name** to the name you would like to give.  
  *NOTE: This setting should be unique.*

* Set **Version** for your ServiceNow instance.  
* Set **Enable OIM** to **Yes**.  
* Set **ServiceNow Application URL** to the URL of your **ServiceNow** instance.  
  Format: `https://<instance name>.service-now.com`  
  E.g: `https://ven01172.service-now.com`  
* Set **ServiceNow User Name** to the admin user name of ServiceNow.  
* Set **ServiceNow User Password** to the corresponding password of the user account that is used in the synchronization.

If the system is deployed on HTTPS and a self-signed certificate is used, then you will have to import the SSL Certificate to be able to access the system from OpsHub Integration Manager. Click [Import SSL Certificates](../getting-started/ssl-certificate-configuration.md) to learn how to import SSL certificate.

# Integration Configuration

In this step, set a time to synchronize data between ServiceNow and the other system to be integrated. Also, define parameters and conditions, if any, for integration.

Click [Step 3 - Configure Integration](http://localhost:90/test/index.php/Step_3_-_Configure_Integration) to learn the step-by-step process to configure integration between two systems.

## Criteria Configuration

**Query**

* Criteria to get entities whose **state** is **Open.**  
  **Example:** `state=1`

* How to get value `1` for the state **Open**?

![snow4](../assets/snow4.png)

Right click on state field and click on Show Choice List.

![snow5](../assets/snow5.png)

Over here we can see the internal value `1` for `Open` state.

**Example:**

* An example of criteria with one 'Lookup field':
state=1^priority=1
state=1^ORstate=2


* An example of criteria with one 'Lookup field and one Date field':
state=1^date_time>2018-01-31 08:00:00


* An example of criteria with 'contains on text field or created by (or some other user field) = sys_id of some user':
sync=true^assigned_to=2a6e8a480fcee600fd4ec3ace1050e20


# Appendix

## Add User

* Open **ServiceNow**.  
* Filter `Users` and click on Users.  
* Click on New.

![snow6](../assets/snow6.png)

* Fill the form details and make sure that active checkbox is enabled.

![snow7](../assets/snow7.png)

* Open created user and click on **Edit Roles**.

![snow8](../assets/snow8.png)

* Add **admin** privileges from Collection and click on Save.

![snow9](../assets/snow9.png)

## Create Custom Field

For creating custom field in ServiceNow follow below steps (Example: Incident Entity)

* Navigate to entity in which you want to add custom field.

![snow10](../assets/snow10.png)

* Open any record

![snow11](../assets/snow11.png)

* Click on additional actions

![snoq12](../assets/snoq12.png)

* Click on new and add entity as shown below

![snow13](../assets/snow13.png)

* Add the field in associated import set table also in same way as above.

## Turning on Auditing for a table

* Navigate to System Definition > Dictionary.

![snow15](../assets/snow15.png)

* Select the table to audit. For example, incident  
* Select the dictionary entry for the table. The table name always has an empty column name and the type of collection.

![snow16](../assets/snow16.png)

* Check the Audit check box.

![snow17](../assets/snow17.png)

* Click Update.

## Create Import Set Table and Transformation Map

* Select OpsHub Integration Solution for ServiceNow application in Settings, as shown below

![snow18](../assets/snow18.png)

* Type Tables in navigator of ServiceNow  
* Click on Tables

![snow19](../assets/snow19.png)

* Click on New

![snow20](../assets/snow20.png)

* Create New Import set table as shown below

![snow21](../assets/snow21.png)

* Make sure you are creating import set table under OpsHub Integration Solution for ServiceNow Application  
* Make sure you are extending Import Set Row (`sys_import_set_row`) Table.

* Create columns as per original Table in your import set table as shown below

![snow22](../assets/snow22.png)

* Create Transformation Map - Type transformation in Navigator as shown below

![snow23](../assets/snow23.png)

* Create New Transformation Map as shown below

![snow24](../assets/snow24.png)

* Map fields as per your requirement - Click on New after submitting above in Field Map

![snow25](../assets/snow25.png)

* In the import set table, create a new field for data type "String"(Refer section 6.41.4.2), and map this new field to Sys ID and make Coalesce "True".

![snow26](../assets/snow26.png)

* For reference field (Link) user source script as shown below.

![snow27](../assets/snow27.png)

### Sample Source Script

```javascript
if(source.<source_field_name>=="-1"){
  target.<target_field_name>="";
}
else if(source.<source_field_name>==""){
}
else{
  target.<target_field_name>=source.<source_field_name>;
}
```

**Internal name of source field and target field can be checked as shown below**

* Open source table (Knowledge in our example)

![snow28](../assets/snow28.png)

* Open column which is of reference type (Category in our example)

![snow29](../assets/snow29.png)

* Internal name for target field can also be checked in the same way as above.

* Source script is supported only for reference type of field.

