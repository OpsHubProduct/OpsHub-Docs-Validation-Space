
# Overview

Objects in [GraphQL](https://graphql.org/graphql-js/object-types/) represent the resources that can be accessed and modified. An object can contain a list of fields of various types.  
Example: [Integration](#integration) is an object for Integration resource which can be used to retrieve and modify the integration configuration and it has fields like name, id, folderId, projectConfiguration, etc.

# Resource Objects

Below are the objects schema details for the different available resources of OpsHub Integration Manager.  
In the below schema structure:  
- **Name**: Represents the name of the field.  
- **Description**: Represents the description of the field.  
- **Type**: Represents the type of the field.  
- **Writable**: Represents whether the field is an input field or not.  
  - * following Yes value indicates the field is mandatory to create operation.  
  - ** following Yes value indicates the field is mandatory to update operation.  
- Mandatory input fields: * preceding Yes value indicates the fields is mandatory.  
- **Readable**: Represents whether the field is an output field or not.  
- **Filterable**: Represents whether the field is filterable field or not in the list API request.

## GlobalFailure

- Global failure contains the details regarding the Global Failure(s) of the integration.  
- Fields:

| **Name**         | **Type**                  | **Description**                                                                 | **Writable** | **Readable** | **Filterable** |
|------------------|---------------------------|----------------------------------------------------------------------------------|--------------|--------------|----------------|
| createdTime      | String                    | Time when the failure is created                                                | No           | Yes          | No             |
| direction        | [Direction](#direction)   | Data synchronization [direction](#direction) of the integration in which the failure has occurred. It is an Enum of type Direction | No | Yes | Yes |
| entityPairId     | int                       | Unique Id reference of the Integration EntityPair in which this failure has occurred | No | Yes | Yes |
| failureCode      | String                    | Corresponds to the failure                                                      | No           | Yes          | Yes            |
| failureCount     | long                      | Number of times the failure has logged                                          | No           | Yes          | No             |
| failureMessage   | String                    | Message of the failure                                                          | No           | Yes          | Yes            |
| failureTrace     | String                    | Trace of failure                                                                | No           | Yes          | No             |
| integrationId    | int                       | Group Id of the integration for which the failure has logged                    | No           | Yes          | Yes            |
| lastUpdatedTime  | String                    | The most recent time when failure is updated                                    | No           | Yes          | Yes#           |

- #: Indicates the filter on this field in not supported directly with this field name.  
  - To filter the global failures with respect to `lastUpdatedTime`, combination of `executionType` and `executionValue` filter is used.

| **Filter Key**    | **Possible Values for the Filter**                              | **Description**                                                |
|------------------|------------------------------------------------------------------|----------------------------------------------------------------|
| executionType     | LAST_CYCLE, LAST_HOURS, LAST_DAYS, LAST_WEEKS, LAST_MONTHS      | Duration type in which we want to query the global failures   |
| executionValue    | 1 for LAST_CYCLE, 1 to 99 for the rest                           | Duration value in which we want to query the global failure   |

- Please refer to the [Use case 1](List_down_the_most_frequent_10_global_failures_of_last_two_months) for list down the failures of last 2 months for example on this filter.

- **Operations:**
  - Query the List of global failure(s)
    - This can be performed with the [globalFailureList](#globalfailurelist) object.
  - Delete the List of global failure(s)
    - This can be performed with the [BulkOperation](#bulkoperation) object.

## Integration

- Integration contains the details regarding the [integration configuration](../integrate/integration-configuration.md) using which we can retrieve or modify the integration.
- Fields:

| **Name**           | **Type**                                      | **Description**                                                                                          | **Writable** | **Readable** | **Filterable** |
|--------------------|-----------------------------------------------|-----------------------------------------------------------------------------------------------------------|--------------|--------------|----------------|
| createdTime        | String                                        | Time when this integration was created                                                                   | No           | Yes          | No             |
| entityPairs        | List<[EntityPair](#entitypair)>              | List of EntityPairs configured in this integration                                                       | Yes*         | Yes          | No             |
| folderId           | Integer                                       | Unique id reference of the Folder containing this integration                                            | Yes*         | Yes          | Yes            |
| id                 | int                                           | Unique Id of this Integration                                                                             | Yes**        | Yes          | Yes            |
| lastUpdatedTime    | String                                        | The most recent time when this integration has been updated                                              | No           | Yes          | Yes            |
| name               | String                                        | Display name of this integration                                                                         | Yes*         | Yes          | Yes            |
| objectVersion      | int                                           | Version of this Integration with respect to its persistent storage in database.                          | Yes**        | Yes          | No             |
| projectConfiguration | [ProjectConfiguration](#projectconfiguration) | Details regarding [Projects](#project) included in this integration configuration for synchronization     | Yes*         | Yes          | No             |
| system1            | Integer                                       | Unique id reference of the system 1 in this integration                                                  | Yes*         | Yes          | Yes#           |
| system2            | Integer                                       | Unique id reference of the system 2 in this integration                                                  | Yes*         | Yes          | Yes#           |

- *: Fields are mandatory in the create operation.  
- **: Fields are mandatory in the update operation along with the mandatory fields of the create operation.  
  - If `objectVersion` field is not mentioned in the request body, then it will give [conflicting operation error](409: Conflict: OH-API-0200).
- #: Indicates the filter on this field is not supported directly with this field name.  
  - To filter the integration list with respect to # marked fields or its some of the sub fields, the below filter key can be used:

| **Fields**                      | **Filter Key**         | **Filter Value**                                                                 |
|----------------------------------|-------------------------|----------------------------------------------------------------------------------|
| system1 or system2              | associatedMapping       | Value corresponds to unique id reference of the system 1 or system 2             |
| mappingId of any entityPairs   | associatedWorkflow      | Value corresponds to unique id reference of the mapping used for entity pair     |
| Status of any entityPairs      | status                  | Value corresponds to the status of the integration. ACTIVE or INACTIVE           |
| Status of any entityPairs      | associatedWorkflow      | Value corresponds to the unique id reference of the workflow                     |

- **Operations**
  - Create Integration
  - Update Integration
  - Delete Integration
    - While deleting the integration, `id` needs to be mentioned in the API request body.
  - Query the list of Integrations
    - This can be performed with the [IntegrationList](#integrationlist) object.
## ProcessingFailure

- ProcessingFailure contains the details regarding the [Processing Failure](Manage_Integration_Failures#Event_Failure_Management_Overview)(s) of the integration.
- Fields:

| **Name**             | **Type**                      | **Description**                                                                                         | **Writable** | **Readable** | **Filterable** |
|----------------------|-------------------------------|----------------------------------------------------------------------------------------------------------|--------------|--------------|----------------|
| createdTime          | String                        | Time when this failure was created                                                                       | No           | Yes          | No             |
| dependentFailureCount| int                           | Number of dependent failures for this failure                                                            | No           | Yes          | No             |
| direction            | [Direction](#direction)       | Data synchronization direction of the integration in which this failure has occurred                     | No           | Yes          | Yes            |
| entityId             | String                        | Source entity id for which this failure has occurred                                                     | No           | Yes          | Yes            |
| entityPairId         | int                           | Unique Id reference of the [EntityPair](#entitypair) in which this failure has occurred                  | No           | Yes          | No             |
| eventXML             | String                        | XML for the event for which this processing failure has occurred                                         | Yes          | Yes          | No             |
| failureCode          | String                        | Failure code corresponds to this failure                                                                 | No           | Yes          | Yes            |
| failureMessage       | String                        | Message of this failure                                                                                  | No           | Yes          | Yes            |
| id                   | int                           | Unique Id of this processing failure                                                                     | Yes**        | Yes          | Yes            |
| integrationId        | int                           | Unique id reference of the integration for which this failure has occurred                               | No           | Yes          | Yes            |
| lastUpdatedTime      | String                        | The most recent time when this failure has been updated                                                  | No           | Yes          | Yes            |
| notified             | Boolean                       | If this failure is notified to the User via [Email notification](Configure_Failure_Notification), then its value will be true | No | Yes | No |
| objectVersion        | int                           | Version of this processing failure to avoid override in parallel usage                                   | Yes**        | Yes          | No             |
| projectName          | String                        | Project name of the source entity for which this failure has occurred                                    | No           | Yes          | No             |
| retryCount           | int                           | Number of times this failure has been retried since last reset of Retry Count                            | Yes          | Yes          | No             |
| totalRetriedCount    | int                           | Total number of times this failure has been retried                                                      | No           | Yes          | No             |
| workflowId           | int                           | Unique Id reference of the workflow, executing which this failure has occurred                           | No           | Yes          | No             |

- **: Indicates the fields are mandatory in the update operation along with the mandatory fields of the create operation.
  - If `objectVersion` is not mentioned in the request body, it will give [conflicting operation error](409: Conflict: OH-API-0200).

- **Operations**  
  - Query the List of processing failure(s):  
    - Performed with [ProcessingFailureList](#processingfailurelist) object.  
  - Update event XML of the processing failure  
  - Perform bulk operations:
    1. Retry list of processing failures with/without dependents  
    2. Delete list of processing failures with/without dependents  
    - Use the [BulkOperation](#bulkoperation) object

# Associated Objects

## Authentication

- Contains the authentication data corresponding to system.
- Fields:

| **Name**     | **Type**                            | **Description**                                |
|--------------|-------------------------------------|------------------------------------------------|
| inputType    | [AuthenticationModeEnum](#authenticationmodeenum) | AuthenticationModeEnum                         |
| parameters   | List<[EaiKeyValue](#eaikeyvalue)>   | List of parameters needed for authentication   |

## ListObjects

### CommonListObjects

- Fields common to every list object of the OpsHub API

| **Name**                | **Type**                          | **Description**                                                                       |
|-------------------------|-----------------------------------|----------------------------------------------------------------------------------------|
| fetchAllAccessibleObjects | Boolean                         | If true, fetches resources in same folder and all parent folders                      |
| filterList              | List<[Filter](#filter)>           | Filters to be used in querying the resources                                          |
| pagination              | [Pagination](#pagination)         | Details of requested page data                                                        |
| sortBy                  | List<[SortOrder](#sortorder)>     | Sorting information                                                                   |

### Filter

- Fields:

| **Name**   | **Type**                             | **Description**                                                                         |
|------------|--------------------------------------|------------------------------------------------------------------------------------------|
| key        | String                               | Field name on which filter is applied (must be filterable)                              |
| operator   | [FilterOperatorType](#filteroperatortype) | Enum of type FilterOperatorType                                                         |
| value      | String                               | Field value to be matched                                                               |

### GlobalFailureList

- Contains the list of global failure(s) of the integration

| **Name** | **Type**                               | **Description**                                 |
|----------|----------------------------------------|--------------------------------------------------|
| list     | List<[GlobalFailure](#globalfailure)>  | List of Global Failures                          |
| All other fields of [CommonListObjects](#commonlistobjects) are applicable |

### IntegrationList

- Contains the list of integrations

| **Name** | **Type**                                | **Description**                                  |
|----------|-----------------------------------------|--------------------------------------------------|
| list     | List<[Integration](#integration)>       | List of Integrations                             |
| All other fields of [CommonListObjects](#commonlistobjects) are applicable |

### ProcessingFailureList

- Contains the list of [Processing Failure](#processingfailure)(s)

| **Name** | **Type**                                  | **Description**                                 |
|----------|-------------------------------------------|--------------------------------------------------|
| list     | List<[ProcessingFailure](#processingfailure)> | List of Processing Failures                    |
| All other fields of [CommonListObjects](#commonlistobjects) are applicable |

### Pagination

- Information on pagination configuration

| **Name**              | **Type**    | **Description**                                  |
|-----------------------|-------------|--------------------------------------------------|
| pageSize              | Integer     | Page size                                        |
| startAt               | Integer     | Start offset                                     |
| totalNumberOfRecords  | Long        | Total number of records                          |

### SortOrder

- Sorting configuration

| **Name**   | **Type**                          | **Description**                                      |
|------------|-----------------------------------|------------------------------------------------------|
| orderType  | [OrderingType](#orderingtype)     | Sorting order                                        |
| sortBy     | String                            | Field to be sorted on                                |

# Bulk Operation Objects

## BulkOperation

- Contains the bulk operation information for mutations

| **Name**     | **Type**                                | **Description**                                                  |
|--------------|-----------------------------------------|------------------------------------------------------------------|
| action       | [BulkOperationAction](#bulkoperationaction) | Enum of BulkOperationAction                                     |
| ids          | List<Integer>                           | List of ids for failures to apply bulk operation                |
| objectType   | [ObjectType](#objecttype)               | ObjectType on which operation is performed                      |
| results      | List<String>                            | Result of bulk operation                                        |

## BulkOperationAction

- Enum values:

| **Value**              | **Description**                              |
|------------------------|----------------------------------------------|
| DELETE                 | Delete operation                             |
| DELETE_WITH_DEPENDENTS | Delete with dependent failures               |
| RETRY_WITH_DEPENDENTS  | Retry with dependent failures                |
| RETRY                  | Retry operation                              |

# Others

## AdvanceSettings

- Contains advanced configuration details for [EntityPair](#entitypair)

| **Name**                  | **Type**                                      | **Description**                                                |
|---------------------------|-----------------------------------------------|----------------------------------------------------------------|
| actionOnDeletedTargetEntities | [ActionOnDeletedEntities](#actionondeletedentities) | Action on deletion in target (Enum)                    |
| criteria                  | [CriteriaSettings](#criteriasettings)         | Criteria configuration                                         |
| maximumRetryCount         | Integer                                       | Retry count for processing failure                             |
| read                      | [OperationAdvanceSettings](#operationadvancesettings) | Advanced read settings                                 |
| readPageSize              | Integer                                       | Page size for reading                                          |
| scheduleId                | Integer                                       | ID of associated schedule                                      |
| skipAbsentFields          | Boolean                                       | Skip fields absent in target                                   |
| syncConfirmationField     | String                                        | End system field name for confirmation                         |
| synchronizationMode       | [IntegrationMode](#integrationmode)           | Mode of synchronization                                        |
| synchronizationType       | [SynchronizationType](#synchronizationtype)   | Type of synchronization                                        |
| syncOnlyCurrentState      | Boolean                                       | Synchronize current state only                                 |
| targetSearch              | [TargetSearchQuery](#targetsearchquery)       | Search in target before sync                                   |
| workflow                  | [WorkflowAssociation](#workflowassociation)   | Workflow association                                           |
| write                     | [OperationAdvanceSettings](#operationadvancesettings) | Advanced write settings                                |

## CriteriaSettings

- Contains criteria configuration details

| **Name**           | **Type**                     | **Description**                                                                     |
|--------------------|------------------------------|--------------------------------------------------------------------------------------|
| query              | String                       | Condition for synchronizing selected entity                                         |
| storageFieldName   | String                       | Field name for criteria storage                                                     |
| storageType        | [StorageType](#storagetype)  | Enum for storage scheme                                                             |

## EaiKeyValue

| **Name** | **Type** | **Description**                                                                            |
|----------|----------|---------------------------------------------------------------------------------------------|
| key      | String   | Unique key for each configuration for the system in OpsHub Integration Manager             |
| value    | Object   | Value (primitive or complex) for the key                                                    |

## EntityPair

- Configuration of entities for synchronization between system1 and system2

| **Name**              | **Type**                        | **Description**                                                                     |
|-----------------------|----------------------------------|--------------------------------------------------------------------------------------|
| direction             | [Direction](#direction)         | Direction of synchronization                                                        |
| entityTypeForSystem1  | [EntityType](#entitytype)       | Entity type for system 1                                                            |
| entityTypeForSystem2  | [EntityType](#entitytype)       | Entity type for system 2                                                            |
| id                    | Integer                         | Unique identifier for the entity pair                                               |
| mappingId             | Integer                         | ID of mapping used                                                                  |
| settings              | [entityPairSettings](#entitypairsettings) | Forward/backward direction settings                                   |

## entityPairSettings

- It contains the details about the configuration for forward and backward direction.
- Fields:

| **Name**   | **Type**                                          | **Description**                                                                 |
|------------|---------------------------------------------------|---------------------------------------------------------------------------------|
| backward   | [EntityPairDirectionalSettings](#entitypairdirectionalsettings) | Details about the entity pair configuration for the backward direction         |
| forward    | [EntityPairDirectionalSettings](#entitypairdirectionalsettings) | Details about the entity pair configuration for the forward direction          |

## EntityPairDirectionalSettings

- It is a GraphQL object, which includes the details about the advanced configuration of the integration and state of the integration.
- Fields:

| **Name**           | **Type**                           | **Description**                                                                                       |
|--------------------|------------------------------------|--------------------------------------------------------------------------------------------------------|
| advanced           | [AdvanceSettings](#advancesettings) | It indicates the [entity specific advanced configurations](integration_configuration#specific-advanced-configuration) |
| executionDetails   | [ExecutionDetails](#execution-details) | It indicates the execution status, i.e., whether the integration is under execution or not            |
| startPollingTime   | String                             | Start polling time for the artifact pair. The format for this time is “Day Mon DD YYYY HH:MM:SS” i.e., Mon Dec 30 2019 09:18:26 |
| status             | [Status](#status)                  | It indicates the status of the integration. It is an enum of type [Status](#status)                  |

## EntityType

- It contains the details about the entity.
- Fields:

| **Name**        | **Type** | **Description**                          |
|------------------|---------|-------------------------------------------|
| displayName     | String  | Display name of the entity               |
| internalName    | String  | Unique internal name corresponds to the entity |

- Here, action, ids and objectType fields needs to be mentioned in the JSON request body and results can be retrieved in the response.

## Execution Details

- It contains the details about the execution of the integration.
- Fields:

| **Name**    | **Type** | **Description**                                       |
|-------------|----------|--------------------------------------------------------|
| executing   | Boolean  | It will be true when the integration is under execution/running |

## OperationAdvanceSettings

- It contains details regarding the system specific [advanced configuration](integration_configuration#advance_settings) of the [entity pair](#entitypair).
- Fields:

| **Name**               | **Type**                                | **Description**                                                                 |
|------------------------|-----------------------------------------|---------------------------------------------------------------------------------|
| overrideParameters     | [OverrideParameters](#overrideparameters) | Details that can be overridden for the system configured in the integration    |
| remoteIdFieldName      | String                                  | Field name of the other system in which the unique id of the entity will be stored for the [traceability](integration_configuration#tracking_id_and_link_of_entities_across_systems) purpose |
| remoteLinkFieldName    | String                                  | Field name of the other system in which the unique id of the entity will be stored for the [traceability](integration_configuration#tracking_id_and_link_of_entities_across_systems) purpose |
| systemSpecificSettings | List<[EaiKeyValue](#eaikeyvalue)>        | Key-value pair for the system specific advance configuration                   |

## OverrideParameters

- It contains details of the system which can be overridden.
- Fields:

| **Name**        | **Type**                   | **Description**                                    |
|------------------|----------------------------|----------------------------------------------------|
| authentication  | [Authentication](#authentication) | Details regarding the authentication data for the system |

## Project

- It contains the details about the Project available in the end system.
- Fields:

| **Name**        | **Type** | **Description**                          |
|------------------|---------|-------------------------------------------|
| displayName     | String  | Display name of the Project              |
| internalName    | String  | Unique internal name corresponds to the project |

## ProjectConfiguration

- It contains details about the configuration of project mapping for data synchronization. This describes project specification for the synchronization of the data, i.e., which project of system1 corresponds to which project of system2.
- Fields:

| **Name**                      | **Type**                                 | **Description**                                                                 |
|-------------------------------|------------------------------------------|---------------------------------------------------------------------------------|
| projectPairs                  | List<[ProjectPair](#projectpair)>        | List of Source and target project pairs along with the data synchronization direction |
| syncChildProjectsForSystem1   | Boolean                                  | Whether the [child project synchronization](../integration-configuration.md#child-project-synchronization) is enabled for the Endpoint 1 |
| ObjectsyncChildProjectsForSystem2ype | Boolean                          | Whether the [child project synchronization](../integration-configuration.md#child-project-synchronization) is enabled for the Endpoint 2 |

## ProjectPair

- It contains details about the project of system1 and project of system2 along with the direction in which the synchronization for the data will be done.
- Fields:

| **Name**             | **Type**                 | **Description**                                                                 |
|----------------------|--------------------------|---------------------------------------------------------------------------------|
| dataSyncDirection    | Direction                | Data synchronization direction for the source and target project pair. It is an Enum of type [Direction](#direction) |
| projectForSystem1    | [Project](#project)      | Project details corresponds to system 1                                         |
| projectForSystem2    | [Project](#project)      | Project details corresponds to system 2                                         |

## TargetSearchQuery

- It contains configuration details of the [search in target before sync](../integrate/integration-configuration.md#search-in-target-before-sync).
- Fields:

| **Name**                 | **Type**                                     | **Description**                                                                 |
|--------------------------|----------------------------------------------|---------------------------------------------------------------------------------|
| actionOnMultipleResults  | [ActionOnMultipleResults](#actiononmultipleresults) | When there are multiple entities satisfy the target lookup query, then the behavior of the synchronization will be decided by this field value. It is Enum of type [ActionOnMultipleResults](#actiononmultipleresults) |
| actionOnNoResult         | [ActionOnNoResults](#actiononnoresults)     | When there is no matching entity found in target system, then the behavior of the synchronization will be decided by this field value. It is Enum of type [ActionOnNoResults](#actiononnoresults) |
| continueSync             | Boolean                                     | If its value is Yes, then sync will be continued for the entities which satisfy the Target Lookup query |
| query                    | String                                      | It is a Target Lookup query, which is used for search entity in the target system in native target system format query |

## WorkflowAssociation

- It contains the details about [workflow](integration_configuration#workflow_association) associated with the integration.
- Fields:

| **Name**        | **Type**                              | **Description**                                                 |
|------------------|----------------------------------------|------------------------------------------------------------------|
| integration     | [WorkflowSettings](#workflowsettings) | Associated workflow details for the integration mode            |
| reconciliation  | [WorkflowSettings](#workflowsettings) | Associated workflow details for the reconciliation mode         |

## WorkflowSettings

- It contains the details about workflow along with the mode in which that workflow will be applicable in the integration configuration.
- Fields:

| **Name**                   | **Type**                                               | **Description**                                                                 |
|----------------------------|--------------------------------------------------------|---------------------------------------------------------------------------------|
| eventTypesToSynchronize   | List<[SynchronizationEventType](#synchronizationeventtype)> | List of event type(s) to be considered for synchronization for which the workflow will be applicable. [SynchronizationEventType](#synchronizationeventtype) is an Enum. |
| id                        | Integer                                                | Unique id reference to the workflow associated with the integration configuration |

# Enums

## Overview

Enums represents the list of possible values for the field.

## Enum Details

### ActionOnDeletedEntities

- It represents the action to be performed when the [entity got deleted in the target system](../integrate/integration-configuration.md#action-on-entity-deleted-in-target).
- Possible values:

| **Value**        | **Description**                                                       |
|------------------|------------------------------------------------------------------------|
| CREATE_FAILURE   | It will create processing failure in OpsHub Integration Manager       |
| RECREATE         | It will re-create the entity in the target system                     |
| SKIP_UPDATE      | It will skip the synchronization of the update                        |

### ActionOnMultipleResults

- It represents the action to be performed when there are multiple entities found in the target system matching the query mentioned in the [Search in target before sync](integration_configuration#search_in_target_before_sync) configuration.
- Possible values:

| **Value**  | **Description**                                          |
|------------|----------------------------------------------------------|
| CONTINUE   | Continue the synchronization of the event               |
| FAIL       | Fail the synchronization and create a processing failure |

### ActionOnNoResults

- It represents the action to be performed when there is no matching entity found in target system for the query mentioned in the [Search in target before sync](../integrate/integration-configuration#search-in-target-before-sync) configuration.
- Possible values:

| **Value** | **Description**                                  |
|-----------|--------------------------------------------------|
| CREATE    | It will create new entity in the target system   |
| SKIP      | It will skip the synchronization for that entity |

### AuthenticationModeEnum

- It represents the supported authentication types by end system.
- Possible values:

| **Value**            | **Description**                                                                 |
|----------------------|---------------------------------------------------------------------------------|
| API_TOKEN            | [API token](https://auth0.com/learn/token-based-authentication-made-easy/) based authentication |
| COOKIE               | Cookie based authentication                                                     |
| OAUTH                | [OAuth](https://oauth.net/2/) authentication scheme                             |
| RSA                  | [RSA](https://community.rsa.com/docs/DOC-77387) based authentication            |
| USERNAME_PASSWORD    | Basic authentication scheme which needs username and password                   |

### Direction

- It represents the data synchronization direction.
- Possible values:

| **Value**     | **Description**                   |
|---------------|-----------------------------------|
| FORWARD       | Forward direction                 |
| BACKWARD      | Backward direction                |
| BIDIRECTIONAL | Forward and backward direction    |

### FilterOperatorType

- It represents the supported filter operators.
- Possible values:

| **Value**     | **Description**                     |
|---------------|-------------------------------------|
| EQUAL         | Equals to operator                  |
| NOT_EQUAL     | Not equals to operator              |
| GT            | Greater than operator               |
| GTE           | Greater than or equals to operator  |
| LIKE          | Operator to select similar values   |
| LT            | Less than operator                  |
| LTE           | Less than or equals to operator     |

### IntegrationMode

- It represents the mode of the integration.
- Possible values:

| **Value**     | **Description**                                          |
|---------------|----------------------------------------------------------|
| INTEGRATION   | [Integration](integration_configuration) mode            |
| RECONCILE     | [Reconciliation](reconciliation) mode                    |

### ObjectType

- It represents the object type for performing the bulk operation.
- Possible values:

| **Value**           | **Description**        |
|---------------------|------------------------|
| GLOBAL_FAILURES     | Global failure         |
| PROCESSING_FAILURES | Processing failure     |

### OrderingType

- It represents the sorting order.
- Possible values:

| **Value**   | **Description**     |
|-------------|---------------------|
| ASCENDING   | Ascending order     |
| DESCENDING  | Descending order    |

### Status

- It represents the status of the integration.
- Possible values:

| **Value**   | **Description**                                                                 |
|-------------|----------------------------------------------------------------------------------|
| ACTIVE      | Active status of the integration indicates that integration is turned on and executed on the selected interval for data synchronization |
| EXECUTE     | This value can be given in the Request body for executing an active integration |
| INACTIVE    | The inactive status of the integration indicates that integration is turned off and not doing any data synchronization |

### StorageType

- It represents the storage type in the [criteria configuration](../integrate/integration-configuration.md#criteria-configuration).
- Possible values:

| **Value**   | **Description**                                                              |
|-------------|------------------------------------------------------------------------------|
| DATABASE    | Database storage type for storing information regarding the criteria satisfying entities |
| END_SYSTEM  | End system storage type for storing information regarding the criteria satisfying entities |

### SynchronizationType

- It represents type of the [event synchronization](../integrate/integration-configuration.md#sync-new-failed-or-both-events) for the integration.
- Possible values:

| **Value** | **Description**                                      |
|-----------|------------------------------------------------------|
| BOTH      | Synchronizing new and failed types of events         |
| FAIL      | Synchronizing new events only                        |
| NEW       | Synchronizing failed events (Processing Failures) only |

### SynchronizationEventType

- It represents the type of the event that will be synchronized via associated [workflow](../integrate/integration-configuration.md#workflow-association)
- Possible values:

| **Value** | **Description**                                       |
|-----------|-------------------------------------------------------|
| CREATE    | Synchronizing entity creation only                    |
| DELETE    | Synchronizing entity deletion only                    |
| SYNC      | Synchronizing creation, deletion and update of the entity |
| UPDATE    | Synchronizing updates on the entity only              |

