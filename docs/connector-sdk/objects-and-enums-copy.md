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
