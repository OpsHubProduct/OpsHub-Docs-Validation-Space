# Overview
Get the projects from the end system that the integration user has access to.  

![Note](../assets/Note.jpg =30x) Return the `OH_NO_PROJECT` if the end system does not have the Projects' structure.  

# API URI
This is the URI OpsHub will execute to call this API:  

```http
GET: /projects?
startIndex=<startIndex>
maxResults=<maxResults>
```

# URI Parameters

| Name        | In    | Required | Type    | Description |
|------------|-------|----------|---------|-------------|
| startIndex | Query | True     | Integer | Start index from which list of projects should be returned |
| maxResults | Query | True     | Integer | Maximum number of projects to be returned by custom connector, starting from startIndex |

# Response Payload

```json
[
  {
    "id": "unique identifier",
    "name": "project name",
    "parentId": "parent project id"
  }
]
```

| Name      | Type            | Required | Description |
|-----------|----------------|----------|-------------|
| id        | Integer or String | True     | Id or internal name of the project |
| name      | String          | True     | Display name of the project |
| parentId  | String          | False    | If end system supports project hierarchy, set the id or internal name of the parent project |

# Examples

## Flat project list

**Example 1:**

```json
[
  {
    "id": "1",
    "name": "Sample Project",
    "parentId": ""
  },
  {
    "id": "2",
    "name": "Demo Project",
    "parentId": ""
  }
]
```
## Example 2

```json
[
  {
    "id": "SAMP",
    "name": "Sample Project",
    "parentId": ""
  },
  {
    "id": "DEMO",
    "name": "Demo Project",
    "parentId": ""
  }
]
```
## Project hierarchy

```json
[
  {
    "id": "root",
    "name": "Main Project",
    "parentId": ""
  },
  {
    "id": "1",
    "name": "Sample Project",
    "parentId": "root"
  },
  {
    "id": "2",
    "name": "Demo Project",
    "parentId": "1"
  },
  {
    "id": "3",
    "name": "Trial Project",
    "parentId": "1"
  }
]
```