# Prerequisites

## User Privileges

* Create one user for TestTrack System, dedicated to OpsHub Integration Manager. User should not be used to do any operations from system’s user interface.
* User should not be used to create or update any entities from TestTrack User-interface. For help on how to add user please refer [Add User](#add-user) in appendix section. For help on how to assign user to groups, please refer [Assign User Privileges](#giving-user-privileges) in the appendix section.

## Configuration Pre-requisite

By default, audit log for the entity type is disabled in TestTrack. For syncing TestTrack entity, user will have to enable audit log for all entities that have to sync in the project.  

Following are steps to enable audit log for Defect entity:

![TT Image1](../assets/TT_Image1.png)

* Choose Tools -> Administration -> Project Options. The Project Options dialog box opens.
* Now, navigate to Compliance and select the entity for which enable audit log is to be enabled (We will select ‘Defects’).
* On the right panel under Logging section, check 'Enable detailed audit trail logging' for defect changes. Under Log Changes section check 'Log all defect record data in the audit trail'.
* If you have more entities, then repeat step 3-4 for each entity (such as Test Cases, Requirements, etc.).
* Click OK. 

## Database Information

Following configuration parameters for the TestTrack project database will be required for creating an integration.
* TestTrack project database type
* TestTrack project database host name
* TestTrack project database name
* TestTrack project database username
* TestTrack project database password

## Reverting Renamed Lookup Field Labels To Default

OpsHub Integration Manager does not support lookup fields (System or Custom) whose label has been renamed to something different. User must revert any such renamed lookup field label to its default value from Tools > Administration > Rename Field Labels option if he wants to sync those fields to and from TestTrack using OpsHub Integration Manager.  

In case they are not reverted, such lookup fields will appear as Text (String) type.

# System Configuration

Before you continue to the integration, you must first configure TestTrack.  
Click [System Configuration](../integrate/system-configuration.md) to learn the step-by-step process to configure a system.  
Refer the screenshot given below for reference.

![TT Image2](../assets/TT_Image2.png)

If the system is deployed on HTTPS and a self-signed certificate is used, then you will have to import the SSL Certificate to be able to access the system from OpsHub Integtation Manager. Click [Import SSL Certificates](../getting-started/ssl-certificate-configuration.md) to learn how to import SSL certificate.

For checking the versions of TestTrack, refer Appendix section [Find Version](#find-version).  
If Database connection is not configured for TestTrack system, then click [Database Configuration](../getting-started/database-configuration.md) to learn how to create database connection.

![TT Image8](../assets/TT_Image8.png)

# Mapping Configuration

Map the fields between TestTrack and the other system to be integrated to ensure that the data between both the systems synchronizes correctly.

Click [Mapping Configuration](../integrate/mapping-configuration.md) to learn the step-by-step process to configure mapping between the systems.  
Click [Mapping Checkpoints](#mapping-checkpoints-for-testtrack-as-destination) to learn about mapping checkpoints for TestTrack as a target system.

# Integration Configuration

Set a time to synchronize data between TestTrack and the other system to be integrated. Also, define parameters and conditions, if any, for integration.

Click [Integration Configuration](../integrate/integration-configuration.md) to learn the step-by-step process to configure integration between two systems.

# Integration behaviour

## Attachment Synchronization

For Test Track Defect entity, there can be multiple reports available [under Detail tab] and each of this report can have multiple attachments.
* While synchronizing attachments from Test Track, all the attachments from all these reports will be synchronized to target.
* While synchronizing attachments to Test Track, all the attachments added into other end system, will be synchronized to 1st report.

Below example will help to understand the attachment synchronization behaviour with bidirectional synchronization.

Lets assume that we have bidirectional integration configured between Test Track Defect and VersionOne Defect with attachment synchronization enabled in mapping configuration.
* If there is Defect 1 having 2 reports and each of them having 1 attachment [lets assume : R1 is attachment of Report 1 and R2 is attachment of Report2], then in VersionOne Defect, 2 attachments [R1,R2] will be visible
* Now if we add, 1 attachment[V1] to VersionOne Defect, that attachment will be synchronized to 1st Report [So Report 1 will have 2 attachments[R1,V1] and Report 2 will have 1 attachment[R2]]
  Report 2 attachments will be untouched and won't be added back to report 1
* If we edit the attachment R1 in VersionOne Defect, that will delete and add the attachment R1 on first report  
  But if we edit the attachment R2 in versionOne, it will be added to Report 1 and the attachment of Report 2 will be as it is [This is because of known limitation]
* There is 1 field Detail, available in Test Track defect entity, if this field is mapped when Test Track is target system, all the attachments will be written to 1st Report and other Reports will have no attachments [This is because of known limitation] 

## Relationship Synchronization

Following are expected behaviors while writing links to TestTrack:
* Links created by OpsHub Integration Manager will have only two entities participating in it. Suppose three defects "def1", "def2", and "def3" are linked by "Related Items" in some source system. These links will be sycned to TestTrack as two different links for all of them. So, for above case, it will be three different links "def1" related to "def2", "def2" related to "def3" and "def3" related to "def1".
* Link won't be added if link type "Require Comment" is enabled for link type. 

Following are expected behaviors while reading links from TestTrack:
* If there are two links having same parent and same set of children, then OpsHub Integration Manager will consider only one link.
* If there are more than 2 items participating in any link, then it will be split in more than one link.

Suppose Requirement "req1" is related to 2 testcase "test1" and "test2" through "Requirement Tested By" type of link (it is one link with single parent and two children). In this case, two links will be synced by OpsHub Integration Manager one with each child "test1" and "test2". 

## Administrative Configurations

Recommended link configurations in TestTrack:
* Set "Limit number of items to:" to 2, so that more than one entity is not participating in link.
* Keep "Require Comment" is disabled. 
* Avoid circular linking of issue for parent/child type of links. It will create ambiguity destination systems as this is noy supported in most of the other systems. 
* Don't change project name once integrations are configured. 

# Criteria Configuration

If you want to specify conditions for synchronizing an entity between TestTrack and the other system to be integrated, you can use the Criteria Configuration feature.  
Go to the Create a Criteria Configuration section on the [Integration Configuration](../integrate/integration-configuration.md) page to learn how to configure criteria.

## Query

Query in TestTrack system is the valid TestTrack project database type specific SQL query which can contain any columns available in TestTrack entities specific database table.  

Following are the tables to look for the column names for entities in TestTrack.

| **Entity Name**            | **Table**   |
|----------------------------|-------------|
| **TestTrack Requirement**  | **REQMNT**  |
| **TestTrack Defect**       | **DEFECTS** |
| **TestTrack TestCase**     | **TESTCASE**|

## Sample Queries

**Criteria Syntax**:  
Allowed operands are all the allowed operands in the database for relational query searches.  

For Requirements of 'Type': 'Business Requirement', the query will be as below:  
`idType=1`  
For Defects of 'Priority': "Immediate", the query will be as below:  
`idPriority=1`  
General Syntax is as below:  
`[FieldName's Column Name_as_in_TestTrack_Database][Relational Query Operand][Field Value_For_Criteria_Processing]`

# Known Limitations

* Information about the fields being mandatory is not getting displayed in the list of fields for the supported entities.
* In TestTrack, some fields of lookup type are getting loaded as Text datatype due to metadata issues. Example of one such field is 'Requirement Type' field of TestTrack Requirement entity.
* String, Text, Numeric, Date, DateTime, User (advanced mapping required), Lookup datatypes are supported while Rich Text, HTML, and Wiki fields are not supported in TestTrack.
* Various functionalities like 'Multiproject Polling, Reconciliation, State Transition, Inline Image, Multi Comment, Target Lookup, Current State Support, and Default Linkage' are not supported in TestTrack.
* Unicode characters are not supported in field names and content in fields.
* OpsHub Integration Manager does not support synchronization of **Computer Config** field present under **Detail** tab in TestTrack **Defect** entity.
* Fields under every possible 'Actions' to be performed on the entities from UI by right clicking on them are not supported. Example of such fields are "Reproduced, Reproduction Steps, Remaining Hours, etc".
* Criteria is supported for only the columns present in the main entity table in TestTrack database. e.g. For requirements, the table is 'REQMNT'.

# Appendix

## Add User

![TT Image3](../assets/TT_Image3.png)

For adding new user follow the following steps:
* Log in to TestTrack as a user with ‘Administration’ security group.
* Choose Create > Users. The Add User form will show.
* Enter the Username, First Name and Password. 
* Select Security Groups ‘Administration’.
* Click the Add button.

## Giving User Privileges

![TT Image4](../assets/TT_Image4.png)

For giving privileges, follow the following steps:
* Log in to TestTrack as a user with Administration security group.
* Choose View > Security Groups. The security groups listing will show.
* Select the appropriate Security Group from the list in which to add the user. And click Edit This will display the Edit Security Groups screen:
* From the left panel select Users in Groups.
* From the right panel in Available Users section select the user(s) which needs to be added to the current security group. Click the Add button.
* Click the OK button. 

## Custom Fields

OpsHub Integration Manager requires a few special fields to be defined on the entity that is being synchronized. These must be set up so that OpsHub Integration Manager can track the integration status of each item.

![TT Image5](../assets/TT_Image5.png)

* Log in to TestTrack as a user with Administration security group.
* Choose Tools > Administration > Custom Fields. The Setup Custom Fields dialog box opens.
* Select the entity type in Type dropdown list. (In this case we will select Defect)
* Click the Add button link, and then click the Add Custom Field link on the presented page. The Add Custom Field screen will display:

![TT Image6](../assets/TT_Image6.png)

* Fill in the Field name, Long label and Field code.
* Select the appropriate Field type field the list. (In our case it is Text Field)
* For Text Field Properties select the Single Line and give length to 255.
* Click the OK button.

## Find Version

For getting TestTrack version follow the given steps:

![TT Image7](../assets/TT_Image7.png)

* Log in to the TestTrack project using TestTrack client.
* Go to Help menu and in that click About TestTrack Client menu item. The TestTrack Client dialog will display.
* Below the Server is the version for the TestTrack server. 

## Mapping Checkpoints for TestTrack as Destination

When TestTrack is the target system, and if there is any mapping that requires Workflow event change, then it is mandatory to map the 'state' too. For example, marking 'Assigned' Requirement to 'Resolved' Requirement, map 'State' and 'Event and Result' both. Ensure that for every mapping, value of 'Resultingstate' (value after ':' in Event & Result) and 'State' element is same.
