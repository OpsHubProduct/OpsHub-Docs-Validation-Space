# Overview

Objects in [GraphQL](https://graphql.org/graphql-js/object-types/) represent the resources that can be accessed and modified. An object can contain a list of fields of various types.  

Example: [Integration](#integration) is an object for Integration resource which can be used to retrieve and modify the integration configuration and it has fields like name, id, folderId, projectConfiguration, etc.   

# Resource Objects

Below are the object schema details for the different available resources of {{SITENAME}}.

In the below schema structure: 

* **Name:** Represents the name of the field.  
* **Description:** Represents the description of the field.  
* **Type:** Represents the type of the field.  
* **Writable:** Represents whether the field is an input field or not.  
  * **Mandatory writable fields:**  
    * `*` following Yes value indicates the field is mandatory to create operation.  
    * `**` following Yes value indicates the field is mandatory to update operation.  
  * **Mandatory input fields:** `*` preceding Yes value indicates the fields is mandatory.  
* **Readable:** Represents whether the field is an output field or not.  
* **Filterable:** Represents whether the field is filterable field or not in the list API request.  

## GlobalFailure

Global failure contains the details regarding the Global Failure(s) of the integration.  

**Fields:**

| Name | Type | Description | Writable | Readable | Filterable |
|------|------|-------------|----------|----------|------------|
| createdTime | String | Time when the failure is created | No | Yes | No |
| direction | [Direction](#Direction) | Data synchronization [direction](#Direction) of the integration in which the failure has occurred. It is an Enum of type Direction | No | Yes | Yes |
| entityPairId | int | Unique Id reference of the Integration EntityPair in which this failure has occurred | No | Yes | Yes |
| failureCode | String | Corresponds to the failure | No | Yes | Yes |
| failureCount | long | Number of times the failure has logged | No | Yes | No |
| failureMessage | String | Message of the failure | No | Yes | Yes |
| failureTrace | String | Trace of failure | No | Yes | No |
| integrationId | int | Group Id of the integration for which the failure has logged | No | Yes | Yes |
| lastUpdatedTime | String | The most recent time when failure is updated | No | Yes | Yes# |

> `#` Indicates the filter on this field is not supported directly with this field name.  
> To filter the global failures with respect to `lastUpdatedTime`, combination of **executionType** and **executionValue** filter is used.

| Filter Key | Possible Values for the Filter | Description |
|------------|-------------------------------|-------------|
| executionType | LAST_CYCLE, LAST_HOURS, LAST_DAYS, LAST_WEEKS, LAST_MONTHS | Duration type in which we want to query the global failures |
| executionValue | 1 for LAST_CYCLE; 1 to 99 for the rest | Duration value in which we want to query the global failure |

Please refer to the [Use case 1](#List_down_the_most_frequent_10_global_failures_of_last_two_months) for listing the failures of last 2 months using this filter.

**Operations:**

* **Query the List of global failure(s)**  
  This can be performed with the [globalFailureList](#GlobalFailureList) object.
* **Delete the List of global failure(s)**  
  This can be performed with the [BulkOperation](#BulkOperation) object.

## Integration

Integration contains the details regarding the [integration configuration](#integration-configuration) using which we can retrieve or modify the integration.  

**Fields:**

| Name | Type | Description | Writable | Readable | Filterable |
|------|------|-------------|----------|----------|------------|
| createdTime | String | Time when this integration was created | No | Yes | No |
| entityPairs | List<[EntityPair](#EntityPair)> | List of EntityPairs configured in this integration | Yes* | Yes | No |
| folderId | Integer | Unique id reference of the Folder containing this integration | Yes* | Yes | Yes |
| id | int | Unique Id of this Integration | Yes** | Yes | Yes |
| lastUpdatedTime | String | The most recent time when this integration has been updated | No | Yes | Yes |
| name | String | Display name of this integration | Yes* | Yes | Yes |
| objectVersion | int | Version of this Integration with respect to its persistent storage in database. This version gets updated with respect to each change being performed on Integration from API or User Interface to avoid override scenarios in parallel usage | Yes** | Yes | No |
| projectConfiguration | [ProjectConfiguration](#ProjectConfiguration) | Details regarding [Projects](#Project) included in this integration configuration for synchronization | Yes* | Yes | No |
| system1 | Integer | Unique id reference of the system 1 in this integration | Yes* | Yes | Yes# |
| system2 | Integer | Unique id reference of the system 2 in this integration | Yes* | Yes | Yes# |


*: *:Indicates the fields are mandatory in the create operation.  
*: **:Indicates the fields are mandatory in the update operation along with the mandatory fields of the create operation.  
:::: *If objectVersion field is not mentioned in the request body, then it will give [[409: Conflict: OH-API-0200|conflicting operation error]].  
*: #:Indicates the filter on this field is not supported directly with this field name.  
::::*To filter the integration list with respect to # marked fields or some of its subfields, the below filter key can be used:

| Fields | Filter Key | Filter Value |
|--------|------------|--------------|
| system1 **or** system2 | associatedMapping | Value corresponds to unique id reference of the system 1 or system 2 in this integration |
| mappingId of any entityPairs | associatedWorkflow | Value corresponds to unique id reference of the mapping used for entity pair |
| Status of any entityPairs | status | Value corresponds to the status of the integration. It can be ACTIVE or INACTIVE |
| Status of any entityPairs | associatedWorkflow | Value corresponds to the unique id reference of the workflow |

* **Operations**  
  **Create Integration**  
  **Update Integration**  
  **Delete Integration**  
  ***While deleting the integration, id needs to be mentioned in the API request body.**  
  **Query the list of Integrations**  
  ***This can be performed with the [[#IntegrationList|IntegrationList]] object.**

### ProcessingFailure
*ProcessingFailure contains the details regarding the [[Manage_Integration_Failures#Event_Failure_Management_Overview|Processing Failure]](s) of the integration.*  

**Fields:**

| Name | Type | Description | Writable | Readable | Filterable |
|------|------|-------------|----------|----------|------------|
| createdTime | String | Time when this failure was created | No | Yes | No |
| dependentFailureCount | int | Number of dependent failures for this failure | No | Yes | No |
| direction | [[#Direction|Direction]] | Data synchronization direction of the integration in which this failure has occurred. It is an Enum of type [[#Direction|Direction]] | No | Yes | Yes |
| entityId | String | Source entity id for which this failure has occurred | No | Yes | Yes |
| entityPairId | int | Unique Id reference of the [[#EntityPair|EntityPair]] in which this failure has occurred | No | Yes | No |
| eventXML | String | XML for the event for which this processing failure has occurred | Yes | Yes | No |
| failureCode | String | Failure code corresponds to this failure | No | Yes | Yes |
| failureMessage | String | Message of this failure | No | Yes | Yes |
| id | int | Unique Id of this processing failure | Yes** | Yes | Yes |
| integrationId | int | Unique id reference of the integration for which this failure has occurred | No | Yes | Yes |
| lastUpdatedTime | String | The most recent time when this failure has been updated | No | Yes | Yes |
| notified | Boolean | If this failure is notified to the User via [[Configure_Failure_Notification|Email notification]], then its value will be true | No | Yes | No |
| objectVersion | int | Version of this processing failure with respect to its persistent storage in database. This version gets updated with respect to each change being performed on Processing failure from API or User Interface to avoid the override scenarios in parallel usage | Yes** | Yes | No |
| projectName | String | Project name of the source entity for which this failure has occurred | No | Yes | No |
| retryCount | int | Number of times, this failure has been retried since last reset of Retry Count | Yes | Yes | No |
| totalRetriedCount | int | Total number of times this failure has been retried | No | Yes | No |
| workflowId | int | Unique Id reference of the workflow, executing which this failure has occurred | No | Yes | No |

*: **:Indicates the fields are mandatory in the update operation along with the mandatory fields of the create operation.  
:::* If objectVersion field is not mentioned in the request body, then it will give [[409: Conflict: OH-API-0200|conflicting operation error]].

**Operations**  
*: Query the List of processing failure(s):  
::* It can be performed with the [[#ProcessingFaliureList|ProcessingFailureList]] object.  
*: Update event XML of the processing failure.  
*: Performing bulk operations on the processing failure.  
::* Two types of bulk operations can be performed:  
::: 1. Retry list of processing failures with/without its dependent failures.  
::: 2. Delete the list of processing failures with/without its dependent failures.  
::* It can be performed with the [[#BulkOperation|BulkOperation]] object.

### Associated Objects

#### Authentication
*It contains the details about the authentication data corresponding to system.*  

**Fields:**

| Name | Type | Description |
|------|------|------------|
| inputType | [[#AuthenticationModeEnum|AuthenticationModeEnum]] | [[#AuthenticationModeEnum|AuthenticationModeEnum]] |
| parameters | List[[#EaiKeyValue|<EaiKeyValue>]] | List of parameters needed for the authentication data |

#### ListObjects

##### CommonListObjects
*This object contains the common fields available to every list object of the OpsHub API.*  

**Fields:**

| Name | Type | Description |
|------|------|------------|
| fetchAllAccessibleObjects | Boolean | Indicates whether the search needs to be done in specific folders or across folders. If it is “true”, then it will fetch the resources in the same folder and all the parent folder above it |
| filterList | List[[#Filter|<Filter>]] | Indicates the filters to be used in querying the resources with filters |
| pagination | [[#Pagination|Pagination]] | Indicates the details regarding the requested page data such as from where the page starts, page length and total number of records |
| sortBy | List[[#SortOrder|<SortOrder>]] | Indicates the information regarding the sorting |

##### Filter
* It contains the information for filter setting.  
* This object can be used to specify the filters in [CommonListObject](#CommonListObjects).

**Fields:**

| Name | Type | Description |
|------|------|-------------|
| key | String | Indicates the key, i.e., Field name on which we want to apply the filter. Any filterable field of the object is a valid field |
| operator | [FilterOperatorType](#FilterOperatorType) | Indicates the operators to be used in the filter operation. It is an Enum of type FilterOperatorType |
| value | String | Indicates the Field name of the object on which we want to apply the sorting |

##### GlobalFailureList
* GlobalFailureList contains the details regarding the list of global failure(s) of the integration.

**Fields:**

| Name | Type | Description |
|------|------|-------------|
| list | List<[GlobalFailure](#GlobalFailure)> | List of Global Failure(s) |
| All the fields of [CommonListObject](#CommonListObjects) | As per the type of [CommonListObject](#CommonListObjects) | All the fields, which are available in [CommonListObject](#CommonListObjects) can be used as fields for this object |

##### IntegrationList
* IntegrationList contains the details regarding the list of the integrations.

**Fields:**

| Name | Type | Description |
|------|------|-------------|
| list | List<[Integration](#Integration)> | List of Integration |
| All the fields of [CommonListObject](#CommonListObjects) | As per the type of [CommonListObject](#CommonListObjects) | All the fields, which are available in [CommonListObject](#CommonListObjects) can be used as fields for this object |

##### ProcessingFailureList
* ProcessingFailureList contains the details regarding the list of [Processing Failure](#ProcessingFailure)(s) of the integration.

**Fields:**

| Name | Type | Description |
|------|------|-------------|
| list | List<[ProcessingFailure](#ProcessingFailure)> | List of Global Failure(s) |
| All the fields of [CommonListObject](#CommonListObjects) | As per the type of [CommonListObject](#CommonListObjects) | All the fields, which are available in [CommonListObject](#CommonListObjects) can be used as fields for this object |

##### Pagination
* It contains the information regarding the pagination configuration.  
* This object is a readable field of the [CommonListObject](#CommonListObjects)  
* With this object, we can configure the pagination settings.

**Fields:**

| Name | Type | Description |
|------|------|-------------|
| pageSize | Integer | Indicates the page size |
| startAt | Integer | Indicates the start offset of the pages from the list of records |
| totalNumberOfRecords | Long | Indicates the total number of records |

##### SortOrder
* It contains the information regarding sorting.  
* This object can be used for the sorting order in [CommonListObject](#CommonListObjects)  

**Fields:**

| Name | Type | Description |
|------|------|-------------|
| orderType | [OrderingType](#OrderingType) | Indicates the sorting order. It is Enum of type [OrderingType](#OrderingType) |
| sortBy | String | Indicates the Field name of the object on which we want to apply the sorting |

#### Bulk Operation Objects

##### BulkOperation
* It contains the information regarding the bulk operation to be performed via mutations.

**Fields:**

| Name | Type | Description |
|------|------|-------------|
| action | [BulkOperationAction](#BulkOperationAction) | Indicates the action to be performed for performing Bulk operation. It is an Enum of type [BulkOperationAction](#BulkOperationAction) |
| ids | List<Integer> | Indicates the list of ids of global failure(s)/event failure(s) for which the bulk operations are to be performed |
| objectType | ObjectType | Indicates the [ObjectType](#ObjectType) on which bulk operation is about to be performed. It is an Enum of [ObjectType](#ObjectType) |
| results | List<String> | Indicates the result of the bulk operation |

##### BulkOperationAction
* It represents the bulk operation type  

**Possible values:**

| Value | Description |
|-------|-------------|
| DELETE | Delete operation |
| DELETE_WITH_DEPENDENTS | Delete operation which will be performed on dependent failure |
| RETRY_WITH_DEPENDENTS | Retry operation which will be performed on dependent failure |
| RETRY | Retry operation |

#### Others

##### AdvanceSettings
* It contains the details about the [advanced configuration](#Integration_Configuration#Advance_Settings) specific to the [EntityPair](#EntityPair).

**Fields:**

| Name | Type | Description |
|------|------|-------------|
| actionOnDeletedTargetEntities | [ActionOnDeletedEntities](#ActionOnDeletedEntities) | Action to be performed on the [deletion of the entity in the target system](#Integration_Configuration#Action_on_Entity_Deleted_in_Target). It is enum of type [ActionOnDeletedEntities](#ActionOnDeletedEntities) |
| criteria | [CriteriaSettings](#CriteriaSettings) | Details of the criteria configuration |
| maximumRetryCount | Integer | [retry count](#Integration_Configuration#Maximum_Retry_Count) for the processing failure |
| read | [OperationAdvanceSettings](#OperationAdvanceSettings) | Entity specific advanced settings for read side of the synchronization |
| readPageSize | Integer | Page size for reading the data from the source system |
| scheduleId | Integer | Unique id reference of the [associated schedule](#integration_Configuration#Associate_Schedule) with the integration |
| skipAbsentFields | Boolean | It will be true if you want to [skip the fields](#Integration_Configuration#Skip_Absent_Field) for the selected entity from source system which are not present in target system |
| syncConfirmationField | String | End system field name for writing the sync confirmation value |
| synchronizationMode | [IntegrationMode](#IntegrationMode) | Mode of the synchronization for the integration. It is enum of the IntegrationMode |
| synchronizationType | [SynchronizationType](#SynchronizationType) | Type of the event synchronization configured in the integration. It is an enum of type [SynchronizationType](#SynchronizationType) |
| syncOnlyCurrentState | Boolean | It will be true if you want to synchronize [current state](#Integration_Configuration#Sync_Only_Current_State) |
| targetSearch | [TargetSearchQuery](#TargetSearchQuery) | Configuration for [search in target before sync](#Integration_Configuration#Search_in_Target_Before_Sync) |
| workflow | [WorkflowAssociation](#WorkflowAssociation) | Reference to the [workflow](#Integration_Configuration#Workflow_Association) associated with the entity pair |
| write | [OperationAdvanceSettings](#OperationAdvanceSettings) | Entity specific advanced settings for write side of the synchronization |


##### CriteriaSettings
* CriteriaSettings contain details of [criteria configurations](#Integration_Configuration#criteria_configuration).

**Fields:**

| Name | Type | Description |
|------|------|-------------|
| query | String | Condition that you want {{SITENAME}} to consider when it synchronizes the selected entity between the source system and the destination system |
| storageFieldName | String | Field name for end system criteria storage |
| storageType | [StorageType](#StorageType) | Type of the criteria storage scheme. It is Enum of type [StorageType](#StorageType) |

##### EaiKeyValue
* It contains the pair in which one field will be the key and the other field will be the value corresponding to that key.

**Fields:**

| Name | Type | Description |
|------|------|-------------|
| key | String | Indicates the unique key for each configuration corresponds to the system available in {{SITENAME}} |
| value | Object | Any type (Primitive/Complex) of value for the key |

##### EntityPair
* It contains the details about the [entities configured in the integration](#Integration_Configuration#Basic_Integration). It specifies the configuration for the synchronization of the data, i.e., which entity of system1 corresponds to which entity of system2.

**Fields:**

| Name | Type | Description |
|------|------|-------------|
| direction | [Direction](#Direction) | Data synchronization direction between the pair of entities. It is an Enum of type [Direction](#Direction) |
| entityTypeForSystem1 | [EntityType](#EntityType) | Entity type details for system 1 |
| entityTypeForSystem2 | [EntityType](#EntityType) | Entity type details for system 2 |
| id | Integer | Unique identifier corresponds to the entity pair |
| mappingId | Integer | Unique id reference to [mapping](#Mapping_Configuration) used for that entity pair |
| settings | [entityPairSettings](#entityPairSettings) | Forward and backward direction settings for the entity pair |

##### entityPairSettings
* It contains the details about the configuration for forward and backward direction.

**Fields:**

| Name | Type | Description |
|------|------|-------------|
| backward | [EntityPairDirectionalSettings](#EntityPairDirectionalSettings) | Details about the entity pair configuration for the backward direction |
| forward | [EntityPairDirectionalSettings](#EntityPairDirectionalSettings) | Details about the entity pair configuration for the forward direction |

##### EntityPairDirectionalSettings
* It is a GraphQL object, which includes the details about the advanced configuration of the integration and state of the integration.

**Fields:**

| Name | Type | Description |
|------|------|-------------|
| advanced | [AdvanceSettings](#AdvanceSettings) | It indicates the [entity specific advanced configurations](#Integration_Configuration#specific advanced configuration) |
| executionDetails | [ExecutionDetails](#Execution_Details) | It indicates the execution status, i.e., whether the integration is under execution or not |
| startPollingTime | String | Start polling time for the artifact pair. The format for this time is “Day Mon DD YYYY HH:MM:SS” i.e., Mon Dec 30 2019 09:18:26 |
| status | [Status](#Status) | It indicates the status of the integration. It is an enum of type [Status](#Status) |

##### EntityType
* It contains the details about the entity.

**Fields:**

| Name | Type | Description |
|------|------|-------------|
| displayName | String | Display name of the entity |
| internalName | String | Unique internal name corresponds to the entity |

* Here, `action`, `ids` and `objectType` fields need to be mentioned in the JSON request body and `results` can be retrieved in the response.

##### ExecutionDetails
* It contains the details about the execution of the integration.

**Fields:**

| Name | Type | Description |
|------|------|-------------|
| executing | Boolean | It will be true when the integration is under execution/running |

##### OperationAdvanceSettings
* It contains details regarding the system specific [advanced configuration](#Integration_Configuration#Advance_Settings) of the [entity pair](#EntityPair).

**Fields:**

| Name | Type | Description |
|------|------|-------------|
| overrideParameters | [OverrideParameters](#OverrideParameters) | Details that can be overridden for the system configured in the integration |
| remoteIdFieldName | String | Field name of the other system in which the unique id of the entity will be stored for the [traceability](#Integration_Configuration#Tracking_Id_and_Link_of_Entities_Across_Systems) purpose |
| remoteLinkFieldName | String | Field name of the other system in which the unique id of the entity will be stored for the [traceability](#Integration_Configuration#Tracking_Id_and_Link_of_Entities_Across_Systems) purpose |
| systemSpecificSettings | List<[EaiKeyValue](#EaiKeyValue)> | Key-value pair for the system specific advance configuration |

##### OverrideParameters
* It contains details of the system which can be overridden.

**Fields:**

| Name | Type | Description |
|------|------|-------------|
| authentication | [Authentication](#Authentication) | Details regarding the authentication data for the system |

##### Project
* It contains the details about the Project available in the end system.

**Fields:**

| Name | Type | Description |
|------|------|-------------|
| displayName | String | Display name of the Project |
| internalName | String | Unique internal name corresponds to the project |

##### ProjectConfiguration
* It contains details about the configuration of project mapping for data synchronization. This describes project specification for the synchronization of the data, i.e., which project of system1 corresponds to which project of system2.

**Fields:**

| Name | Type | Description |
|------|------|-------------|
| projectPairs | List<[ProjectPair](#ProjectPair)> | List of Source and target project pairs along with the data synchronization direction |
| syncChildProjectsForSystem1 | Boolean | Whether the [child project synchronization](#Integration_Configuration#Child_Project_Synchronization) is enabled for Endpoint 1 |
| ObjectsyncChildProjectsForSystem2ype | Boolean | Whether the [child project synchronization](#Integration_Configuration#Child_Project_Synchronization) is enabled for Endpoint 2 |

##### ProjectPair
* It contains details about the project of system1 and project of system2 along with the direction in which the synchronization for the data will be done.

**Fields:**

| Name | Type | Description |
|------|------|-------------|
| dataSyncDirection | Direction | Data synchronization direction for the source and target project pair. It is an Enum of type [Direction](#Direction) |
| projectForSystem1 | [Project](#Project) | Project details corresponds to system 1 |
| projectForSystem2 | [Project](#Project) | Project details corresponds to system 2 |

##### TargetSearchQuery
* It contains configuration details of the [search in target before sync](#Integration_Configuration#Search_in_Target_Before_Sync).

**Fields:**

| Name | Type | Description |
|------|------|-------------|
| actionOnMultipleResults | [ActionOnMultipleResults](#ActionOnMultipleResults) | When there are multiple entities satisfying the target lookup query, the behavior of the synchronization will be decided by this field value. It is Enum of type [ActionOnMultipleResults](#ActionOnMultipleResults) |
| actionOnNoResult | [ActionOnNoResults](#ActionOnNoResults) | When there is no matching entity found in target system, the behavior of the synchronization will be decided by this field value. It is Enum of type [ActionOnNoResults](#ActionOnNoResults) |
| continueSync | Boolean | If its value is Yes, then sync will be continued for the entities which satisfy the Target Lookup query |
| query | String | Target Lookup query used for searching entity in the target system in native target system format |

##### WorkflowAssociation
* It contains the details about [workflow associated with the integration](#Integration_Configuration#Workflow_Association).

**Fields:**

| Name | Type | Description |
|------|------|-------------|
| integration | [WorkflowSettings](#WorkflowSettings) | Associated workflow details for the integration mode |
| reconciliation | [WorkflowSettings](#WorkflowSettings) | Associated workflow details for the reconciliation mode |

##### WorkflowSettings
* It contains the details about workflow along with the mode in which that workflow will be applicable in the integration configuration.

**Fields:**

| Name | Type | Description |
|------|------|-------------|
| eventTypesToSynchronize | List<[SynchronizationEventType](#SynchronizationEventType)> | List of event type(s) to be considered for synchronization for which the workflow will be applicable. [SynchronizationEventType](#SynchronizationEventType) is an Enum |
| id | Integer | Unique id reference to the workflow associated with the integration configuration |

### Enums

#### Overview
Enums represent the list of possible values for a field.

#### Enum Details

##### ActionOnDeletedEntities
* Represents the action to be performed when the [entity got deleted in the target system](#Integration_Configuration#Action_on_Entity_Deleted_in_Target).

**Possible values:**

| Value | Description |
|-------|-------------|
| CREATE_FAILURE | It will create processing failure in {{SITENAME}} |
| RECREATE | It will re-create the entity in the target system |
| SKIP_UPDATE | It will skip the synchronization of the update |

##### ActionOnMultipleResults
* Represents the action to be performed when there are multiple entities found in the target system matching the query mentioned in the [Search in target before sync](#Integration_Configuration#Search_in_Target_Before_Sync) configuration.

**Possible values:**

| Value | Description |
|-------|-------------|
| CONTINUE | Continue the synchronization of the event |
| FAIL | Fail the synchronization and create a processing failure |

##### ActionOnNoResults
* Represents the action to be performed when there is no matching entity found in target system for the query mentioned in the [Search in target before sync](#Integration_Configuration#Search_in_Target_Before_Sync) configuration.

**Possible values:**

| Value | Description |
|-------|-------------|
| CREATE | It will create new entity in the target system |
| SKIP | It will skip the synchronization for that entity |

##### AuthenticationModeEnum
* Represents the supported authentication types by end system.

**Possible values:**

| Value | Description |
|-------|-------------|
| API_TOKEN | [API token](https://auth0.com/learn/token-based-authentication-made-easy/) based authentication |
| COOKIE | Cookie based authentication |
| OAUTH | [OAuth](https://oauth.net/2/) authentication scheme |
| RSA | [RSA](https://community.rsa.com/docs/DOC-77387) based authentication |
| USERNAME_PASSWORD | Basic authentication scheme which needs username and password |

##### Direction
* Represents the data synchronization direction.

**Possible values:**

| Value | Description |
|-------|-------------|
| FORWARD | Forward direction |
| BACKWARD | Backward direction |
| BIDIRECTIONAL | Forward and backward direction |

##### FilterOperatorType
* Represents the supported filter operators.

**Possible values:**

| Value | Description |
|-------|-------------|
| EQUAL | Equals to operator |
| NOT_EQUAL | Not equals to operator |
| GT | Greater than operator |
| GTE | Greater than or equals to operator |
| LIKE | Operator to select similar values |
| LT | Less than operator |
| LTE | Less than or equals to operator |

##### IntegrationMode
* Represents the mode of the integration.

**Possible values:**

| Value | Description |
|-------|-------------|
| INTEGRATION | [Integration](#Integration_Configuration) mode |
| RECONCILE | [Reconciliation](#Reconciliation) mode |

##### ObjectType
* Represents the object type for performing the bulk operation.

**Possible values:**

| Value | Description |
|-------|-------------|
| GLOBAL_FAILURES | Global failure |
| PROCESSING_FAILURES | Processing failure |

##### OrderingType
* Represents the sorting order.

**Possible values:**

| Value | Description |
|-------|-------------|
| ASCENDING | Ascending order |
| DESCENDING | Descending order |

##### Status
* Represents the status of the integration.

**Possible values:**

| Value | Description |
|-------|-------------|
| ACTIVE | Integration is turned on and executed on the selected interval for data synchronization |
| EXECUTE | This value can be given in the Request body for executing an active integration |
| INACTIVE | Integration is turned off and not doing any data synchronization |

##### StorageType
* Represents the storage type in the [criteria configuration](#Integration_Configuration#Criteria_Configuration).

**Possible values:**

| Value | Description |
|-------|-------------|
| DATABASE | Database storage type for storing information regarding the criteria satisfying entities |
| END_SYSTEM | End system storage type for storing information regarding the criteria satisfying entities |

##### SynchronizationType
* Represents type of the [event synchronization](#Integration_Configuration#Sync_New.2C_Failed.2C_or_Both_Events) for the integration.

**Possible values:**

| Value | Description |
|-------|-------------|
| BOTH | Synchronizing new and failed types of events |
| FAIL | Synchronizing new events only |
| NEW | Synchronizing failed events (Processing Failures) only |

##### SynchronizationEventType
* Represents the type of the event that will be synchronized via associated [workflow](#Integration_Configuration#Workflow_Association).

**Possible values:**

| Value | Description |
|-------|-------------|
| CREATE | Synchronizing entity creation only |
| DELETE | Synchronizing entity deletion only |
| SYNC | Synchronizing creation, deletion, and update of the entity |
| UPDATE | Synchronizing updates on the entity only |


