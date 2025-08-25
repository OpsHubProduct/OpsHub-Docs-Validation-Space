# Overview
With the {{SITENAME}} API, the user can communicate with {{SITENAME}} where the defined format needs to be used for making the API Calls. The below sections will help you with the format and examples around it and give an idea of the generic API format.

# Format
* **Request Method Type**: GET/POST/PUT/DELETE
* **Request URL**: <Instance API URL>[?query=<Encoded Query Structure>]
* **Request Body**: [JSON request body]
* **Authentication Data**: {{SITENAME}} user credentials
* **Headers**: api_version:1, Content-Type: application/json

**Explanation:**

* **Request URL**
  * It contains <Instance API URL> and optional parameter [?query=<Encoded Query Structure>]. For reading the data from the {{SITENAME}}, the query parameter is needed with the encoded query structure.
  * **Instance API URL**
    * It is an API URL specific to your {{SITENAME}} instance. For any API call to be performed for your instance, it would be a common URL with additional details around operation to be performed.
    * Its format is predefined, which is formed with the details of {{SITENAME}} instance and a static postfix.  
      `<Protocol>://<Host Name/IP address of {{SITENAME}} instance>:<Port Number>/<API endpoint>`

| Element | Description |
|--------|-------------|
| `<Protocol>` | Http/https based on your {{SITENAME}} instance setup |
| `<Host Name/IP address of {{SITENAME}} instance>` | IP address or the configured host name for {{SITENAME}} instance |
| `<Port Number>` | Port number of your {{SITENAME}} instance. Default port for the HTTP is 8989 and HTTPS is 8443 |
| `<API endpoint>` | OpsHubWS/queryNode/execute |

* **Request Body**
  * For modifying the data of the {{SITENAME}} [JSON](https://www.json.org/json-en.html) request body is mentioned in the API request.

* **Authentication Data**
  * {{SITENAME}} API supports Basic Authentication, and so a valid “Username” and “Password” need to be mentioned in each API request.
  * Based on the format of the platform used for invoking the {{SITENAME}} API, user credentials are set at different levels:
    * In the API clients like [postman](https://www.postman.com/), there is a separate section of Authorization for setting this data.
    * In the [curl](https://curl.se/) command, credentials are mentioned with option –u.
    * In the programs written in any programming language, credentials are set based on the expectation of the library which supports HTTP communication

* **Headers**
  * Below API headers need to be mentioned in each API request:
    * api_version:1  
      * It is the required static header in all the {{SITENAME}} API request.
    * Content-Type: application/json  
      * {{SITENAME}} API uses JSON format for data exchange, and so this header is required.
  * Based on the format of the platform used for invoking the {{SITENAME}} API, headers are set at different levels:
    * In the API clients like [postman](https://www.postman.com/), there is a separate section of Headers for setting this data.
    * In the [curl](https://curl.se/) command, headers are mentioned with option –header.
    * In the programs written in any programming language, headers are set based on the expectation of the library that supports HTTP communication.

# Operations supported in API

Two types of operations are supported in {{SITENAME}} API:

## Queries[/Read]
Queries can be used to perform read operations via {{SITENAME}} API. For example, reading the configurations like integration or reading the failures details.  
Please refer to [GraphQL API query](https://graphql.org/learn/queries/) for basic understanding of GraphQL Query.

## Basic Queries

### Format
* **Request Method Type**: GET [It refers to the HTTP GET request]
* **Request URL**: <Instance API URL>?query=<Encoded Query Structure>

**Explanation:**
* **Instance API URL**: Refer to Instance API URL in the Explanation of [Query format](#format).
* **?query**: This is a static keyword indication for query.
* **<Encoded Query Structure>**
  * The details of the object to be retrieved along with its fields list is to be specified here in encoded format.
  * Below is a sample of decoded query structure:

```graphql
query {
  <ObjectName>[(id:<value>)] {
    <Readable Field1, Readable Field2, Readable Field3 ...>
  }
}
```

**Explanation:**
* `<ObjectName>`: For any information retrieval is actually an [object](objects-and-enums.md). Refer to object list for usage.
* `[(id:<value>)]`: If we want to fetch details of the object with specific unique id.
* `{<Readable Fields>}`: Fields of the object that we want to retrieve. For complex fields, mention nested subfields.
* Use any [percent-encoding](https://en.wikipedia.org/wiki/Percent-encoding) tool to encode this.

# Examples

## Retrieve the global failure with the ID:1

* Request Method Type: GET  
* Request URL:  
  ```
  http://10.13.27.222:8989/OpsHubWS/queryNode/execute?query=query%7BglobalFailure(id%3A1)%7BfailureMessage%2CfailureCode%7D%7D
  ```

Decoded:
```graphql
query {
  globalFailure(id:1) {
    failureMessage,
    failureCode
  }
}
```

## Retrieve the list of global failures

* Request Method Type: GET  
* Request URL:  
  ```
  http://10.13.27.222:8989/OpsHubWS/queryNode/execute?query=query%7BglobalFailureList%7Blist%7Bid%2CfailureMessage%2CfailureCode%7D%7D%7D
  ```

Decoded:
```graphql
query {
  globalFailureList {
    list {
      id,
      failureMessage,
      failureCode
    }
  }
}
```
# Advanced Queries

{{SITENAME}} API queries for list objects (integration list, global failure list, event failure list) supports the advanced queries with the [Filters](#queries-with-filters), [Sorting](#queries-with-sorting), and [Pagination](#queries-with-pagination).

## Queries with Pagination

* Pagination is an extension to the list query request to retrieve the data list in paginated way.
* Request format is same as the Basic Queries format with a minor change in the query structure format.

Query structure:
```graphql
query {
  <ObjectName>(pagination:{startAt:<value>, pageSize:<value>}) {
    list {<fields>}
    pagination {pageSize, startAt, totalNumberOfRecords}
  }
}
```

**Example:**

Retrieve global failures with pagination (first 15 records):
* Request Method Type: GET  
* Request URL:  
  ```
  http://10.13.27.222:8989/OpsHubWS/queryNode/execute?query=query%7BglobalFailureList(pagination%3A%7BpageSize%3A15%2CstartAt%3A0%7D)%7Blist%7Bid%2CfailureMessage%2CfailureCode%7D%2Cpagination%3A%7BpageSize%2CstartAt%2CtotalNumberOfRecords%7D%7D%7D
  ```

Decoded:
```graphql
query {
  globalFailureList(pagination:{pageSize:15,startAt:0}) {
    list {
      id,
      failureMessage,
      failureCode
    },
    pagination {
      pageSize,
      startAt,
      totalNumberOfRecords
    }
  }
}
```

## Queries with Sorting

* Sorting is used to retrieve the data in sorted way.
* Request format is same as the Basic Queries format with an additional `sortBy` parameter.

Query structure:
```graphql
query {
  <ObjectName>(sortBy:[{orderType:"ASCENDING",sortBy:"<field>"}]) {
    list {<fields>}
  }
}
```

**Example:**

Retrieve global failures sorted by failure code (ascending):
* Request Method Type: GET  
* Request URL:  
  ```
  http://localhost:8989/OpsHubWS/queryNode/execute?query=query%7BglobalFailureList(sortBy%3A%5B%7BorderType%3A%22ASCENDING%22%2CsortBy%3A%22failureCode%22%7D%5D)%7Blist%7Bid%2CfailureMessage%2CfailureCode%7D%7D%7D
  ```

Decoded:
```graphql
query {
  globalFailureList(sortBy:[{orderType:"ASCENDING",sortBy:"failureCode"}]) {
    list {
      id,
      failureMessage,
      failureCode
    }
  }
}
```

## Queries with Filters

* Filter is an extension to retrieve only matching records based on conditions.

Query structure:
```graphql
query {
  <ObjectName>(filterList:[{key:"<field>", value:"<value>", operator:"EQUAL"}]) {
    list {<fields>}
  }
}
```

**Example:**

Retrieve global failures for integration group with ID 1:
* Request Method Type: GET  
* Request URL:  
  ```
  http://localhost:8989/OpsHubWS/queryNode/execute?query=query%7BglobalFailureList(filterList%3A%5B%7Bkey%3A%22integrationId%22%2Cvalue%3A%221%22%2Coperator%3A%22EQUAL%22%7D%5D)%7Blist%7Bid%2CfailureMessage%2CfailureCode%7D%7D%7D
  ```

Decoded:
```graphql
query {
  globalFailureList(filterList:[{key:"integrationId",value:"1",operator:"EQUAL"}]) {
    list {
      id,
      failureMessage,
      failureCode
    }
  }
}
```

# Mutations[/Write]

Mutations are used to perform write operations via {{SITENAME}} API, such as creating/updating/deleting configurations.

Please refer to [GraphQL Mutations](https://graphql.org/graphql-js/mutations-and-input-types/) for details.

## Format

* **Request Method Type**: POST/DELETE/PUT  
* **Request URL**: <Instance API URL>  
* **Request Body**: JSON request body

JSON structure:
```json
{
  "query": "mutation { <ObjectName>(<fields>) { <response fields> } }"
}
```

**Explanation:**

* `query`: Static key in the JSON body
* `<ObjectName>`: Target object (e.g., integration, globalFailure)
* `<fields>`: Writable fields with values to be modified
* `{<response fields>}`: Fields to retrieve in response

Example:
```graphql
mutation {
  integration(
    id: 1,
    name: "Demo_Integration",
    system1: 2,
    system2: 3
  ) {
    id,
    name,
    folderId,
    createdTime
  }
}
```

**Note:** If mutation structure contains reserved JSON characters, they must be [escaped](../forimg-calls-with-api#json_string_escaping).

# Examples

## Create Integration

- Let's take an example where we want to create a bidirectional integration between two systems with below specifications:
  - Systems involved:
    - System1:
      - Jira [pre-created in {{SITENAME}} with ID 2]
    - System2:
      - Micro Focus ALM/QC [pre-created in {{SITENAME}} with ID 3]
  - Entities involved:
    - System1:
      - Bug [EntityType(internalName:10004)]
    - System2:
      - Defect [EntityType(internalName:defects)]
  - Projects Involved
    - System1:
      - System1_Project1[Project(internalName:10104)]
      - System1_Project2[Project(internalName:10105)]
    - System2:
      - System2_Project1[Project(internalName:DEFAULT:: System2_Project1)]
      - System2_Project2[Project(internalName:DEFAULT:: System2_Project2)]

- Here is the API Request to configure a bidirectional integration which can be used to synchronize the data between Bug entity of Jira and Defect entity of Micro Focus ALM/QC where the data of projects, System1_Project1 and System2_Project1 are in sync, and System1_Project2 and System2_Project2 are in sync.
- For this integration configuration, we will be communicating with [Integration](objects-and-enums.md#integration) Object.

**Request Method Type:** POST  
**Request URL:** `http://10.13.27.222:8989/OpsHubWS/queryNode/execute`  
**Request body:**
```json
{
  "query": "mutation{integration(name:\" Jira_HP_Integration\",system1:2,system2:3,projectConfiguration:{projectPairs:[{projectForSystem1:{internalName:\"10104\"},direction:\"BIDIRECTIONAL\",projectForSystem2:{internalName:\"DEFAULT:: System2_Project1\"}}, {projectForSystem1:{internalName:\"10105\"},direction:\"BIDIRECTIONAL\",projectForSystem2:{internalName:\"DEFAULT:: System2_Project2\"}}]},entityPairs:[{entityTypeForSystem1:{internalName:\"10004\"},direction:\"BIDIRECTIONAL\",entityTypeForSystem2:{internalName:\"defects\"},mappingId:5,settings:{forward:{startPollingTime:\"Mon Dec 30 2019 09:18:26\",advanced:{maximumRetryCount:8,scheduleId:0,synchronizationType:\"BOTH\",workflow:{integration{id:1,eventTypesToSynchronize:[\"CREATE\",\"UPDATE\",\"DELETE\"]}}}},backward:{startPollingTime:\"Mon Dec 30 2019 09:18:26\",advanced:{maximumRetryCount:8,scheduleId:0,synchronizationType:\"BOTH\",workflow:{integration:{id:1,eventTypesToSynchronize:[\"CREATE\",\"UPDATE\"]}}}}}}],folderId:0){id,name,folderId,createdTime,lastUpdatedTime}}"
}
```

## Update Integration

- Let's consider we have an integration configured in {{SITENAME}} with id 1, and we want to update this integration [Criteria](Integration_Configuration#Criteria_Configuration) for synchronizing only the entities having Id>0 for forward direction of the integration.

- To form the request for updating the integration, we need the details for the integration. To retrieve the details of the integration, query given in [example](Forming_Calls_with_API#Example) 1 can be used in which id will be 1, and the object to be retrieved will be [Integration](objects-and-enums.md#integration).

**Request Method Type:** PUT  
**Request URL:** `http://10.13.27.222:8989/OpsHubWS/queryNode/execute`  
**Request body:**
```json
{
  "query": "mutation{integration(id:1,name:\"Jira_HP_Integration\",system1:2,system2:3,projectConfiguration:{projectPairs:[{projectForSystem1:{internalName:\"10104\"},direction:\"BIDIRECTIONAL\",projectForSystem2:{internalName:\"DEFAULT:: System2_Project1\"}}, {projectForSystem1:{internalName:\"10105\"},direction:\"BIDIRECTIONAL\",projectForSystem2:{internalName:\"DEFAULT:: System2_Project2\"}}]},entityPairs:[{entityTypeForSystem1:{internalName:\"10004\"},direction:\"BIDIRECTIONAL\",entityTypeForSystem2:{internalName:\"defects\"},mappingId:5,settings:{forward:{startPollingTime:\"Mon Dec 30 2019 09:18:26\",advanced:{criteria:{query:\"id>0\",storageType:\"DATABASE\"},maximumRetryCount:8,scheduleId:0,synchronizationType:\"BOTH\",workflow:{integration:{id:1,eventTypesToSynchronize:[\"CREATE\",\"UPDATE\",\"DELETE\"]}}}},backward:{startPollingTime:\"Mon Dec 30 2019 09:18:26\",advanced:{maximumRetryCount:8,scheduleId:0,synchronizationType:\"BOTH\",workflow:{integration:{id:1,eventTypesToSynchronize:[\"CREATE\",\"UPDATE\"]}}}}}}],folderId:0,objectVersion:0){id,name,folderId,createdTime,lastUpdatedTime}}"
}
```

## Delete Integration

Let's consider we have an integration configured in {{SITENAME}} with id 1, and if we want to delete that integration, then below API request can be used:

**Request Method Type:** DELETE  
**Request URL:** `http://10.13.27.222:8989/OpsHubWS/queryNode/execute`  
**Request body:**
```json
{
  "query": "mutation{integration(id:1){id}}"
}
```

## Bulk Operations

Two types of bulk operations are supported:

**1. Update**

- **Retrying the failure data**  
  - Suppose we have listed down all the processing failures using queries and we want to retry the processing failures with the id 4,5 and 6, then below mutation can be used:

**Request Method Type:** PUT  
**Request URL:** `http://10.13.27.222:8989/OpsHubWS/queryNode/execute`  
**Request body:**
```json
{
  "query": "mutation{bulkOperation(ids:[4,5,6],objectType:\"PROCESSING_FAILURES\",action:\"RETRY\"){results}}"
}
```

  - Similarly, suppose we want to retry these failures with its dependent failure, then “RETRY_WITH_DEPENDENTS” can be mentioned for the action field in above mutation structure.

**2. Delete**

- **Deleting the failure data**  
  - Suppose we have listed down all the global failures using queries and we want to delete the global failures with the id 4,5 and 6, then below mutation can be used:

**Request Method Type:** DELETE  
**Request URL:** `http://10.13.27.222:8989/OpsHubWS/queryNode/execute`  
**Request body:**
```json
{
  "query": "mutation{bulkOperation(ids:[4,5,6],objectType:\"GLOBAL_FAILURES\",action:\"DELETE\"){results}}"
}
```

  - Suppose we want to delete the event failures with the ids 4,5 and 6, then “PROCESSING_FAILURES” can be mentioned for the “objectType” field in above mutation structure.

  - Suppose we want to delete the event failures along with its dependent event failures with the ids 4,5 and 6, then “DELETE_WITH_DEPENDENTS” can be mentioned for the action field in the above mutation structure.

# Appendix

## JSON string escaping

In the JSON format, some characters like ‘\\’, ‘"’, new line, tab, carriage return, form feed, and backspace are reserved. Hence, these characters must be escaped by replacing them with some other characters. Below are some examples:

- **Backspace** with `\b`
- **Form feed** with `\f`
- **Newline** with `\n`
- **Carriage return** with `\r`
- **Tab** with `\t`
- **Double quote** with `\"`
- **Backslash** with `\\`

>**Note**: Some online tools are available for escaping the reserved characters.



