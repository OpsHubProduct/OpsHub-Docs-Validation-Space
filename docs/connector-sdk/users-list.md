# Overview
Returns the list of users matching the given email, username, or display name in the given project id. Implementing this API will enable OpsHub to automatically map users across the connectors if users have the same email ID, username, or display name. In the absence of this API, the OpsHub admin will have to map users from the mapping interface.

# API URI
```bash
GET /users?
    email=<email>
    &username=<username>
    &displayName=<displayName>
    &projectId=<projectId>
```


# URI Parameters
| **Name**      | **In** | **Required** | **Type** | **Description** |
|---------------|--------|--------------|----------|-----------------|
| email         | Query  | One and only one of these value will come to filter users | String | Return users exactly matching the given email |
| username      | Query  | One and only one of these value will come to filter users | String | Return users exactly matching the given user name |
| displayName   | Query  | One and only one of these value will come to filter users | String | Return users exactly matching the given display name |
| projectId     | Query  | True         | String   | Matching users should belong to a given project only, i.e., they should have permission for the given project to be an assignee, a reporter or should be visible in any other user field |

# Request Payload
```json
[
  { 
    "id": "", 
    "username": "", 
    "email": "", 
    "displayName": "" 
  }, 
  { 
    "id": "", 
    "username": "", 
    "email": "", 
    "displayName": "" 
  } 
]
```

# Response Parameters
| **Name**     | **Required** | **Type** | **Description** |
|--------------|--------------|----------|-----------------|
| id           | True         | String   | Unique id for the user. If the end system does not have a user id, then send the username |
| Username     | True         | String   | Username of the user |
| email        | False        | String   | Email id of the user |
| displayName  | False        | String   | The display name is visible on the end system UI for the given user |

# Examples

**Request**
```bash
GET /users? 
    email=a.b@c.com      
    &projectId=100
```

# Response 

```json
[
  { 

    "id": "101", 

    "username": "user.name", 

    "email": "a.b@c.com", 

    "displayName": "John Doe" 

  }, 

  { 

    "id": "102", 

    "username": "user2.name", 

    "email": "a.b@c.com", 

    "displayName": "User2 Name" 

  } 

]

```


